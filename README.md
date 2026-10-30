# ZUNFI — Android Updates

This is the **public release channel** for ZUNFI Android. Android source code and internal
development remain in the separate, **private** `zunfi/zunfi-android` repository.

## Releases

Stable ZUNFI APKs will appear under **Releases**:
https://github.com/zunfi/zunfi-updates/releases/latest

**Current status: Not yet published.** The app's updater shows "Update channel not published yet"
until the first signed, non-prerelease GitHub Release exists.

Each official release must contain:

- A single Android installable asset named **`ZUNFI.apk`**.
- A tag like **`v0.1.2`**, with matching app `versionName` and an increasing `versionCode`.
- The *same permanent signing certificate* used by the previous installable public release.
- A GitHub-provided SHA-256 digest for the APK.

The in-app updater checks this public channel, downloads the asset, validates the
download size / checksum and Android package name, and opens the **Android system installer**
for user confirmation. The app does not silently install APKs.

## Signing and safety

The private signing keystore, passwords, and GitHub publishing token must **never** be stored
in this public repository, embedded in the APK, or pasted into issues.

A permanent signing keystore must be backed up securely outside GitHub. Losing the signing
key prevents updates to existing installations unless the distribution signing arrangement
supports key recovery or rotation.

Initial testers with earlier **debug** APKs may need to uninstall that debug build once before
installing the first permanently signed ZUNFI release, because debug builds are generally
signed with a different certificate.

## Maintainer workflow

From `zunfi/zunfi-android` Actions, run **ZUNFI Signed Release** after the private signing
secrets and publish token are configured. The workflow publishes a verified, signed `ZUNFI.apk`
here as a GitHub Release.

This repository is only for distributing installable APKs; it does not handle user accounts,
subscription validation, or internet relay traffic.
