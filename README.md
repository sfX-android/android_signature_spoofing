# android_signature_spoofing
patches to provide signature spoofing based on official microG patches with security adjustments.

## about

Based on an user request I reviewed the way how the microG patch
works and the impact of enabling signature spoofing.

The review & my personal conclusion can be found here:
Suicide-Squirrel/issues_pie#30

The implementation has been done as follows:

1. Signature spoofing is globally *disabled* by default
2. Enabling signature spoofing globally is done by a new added switch in developer options
     (key: allow_signature_fake)
3. When enabled and an app asks for signature spoofing a warning dialog is shown (Allow/Reject)
    - note: a log entry will be generated as well
4. When signature spoofing is not enabled it will be silently denied
5. Once signature spoofing has been allowed for an app it can be revoked when needed in:
     "Apps - Advanced - App Permissions - Spoof Package Signature"
6. When an app got the permission and signature spoofing will be disabled again in developer options
     any previously allowed app will be (silently) denied again

The idea was to give the user the choice to get independent from Google where microG comes into play.
The way it has been implemented is similar  to "adb root" which comes pre-shipped with LOS but is also
disabled by default.
Besides that many users running custom ROMs have root installed while using signature spoofing
has its own risks, ofc.

.. but I like the freedom of choice. So here it is :)
