## Disable TPM Guide

:::warning
This process modifies UEFI source files.  
Incorrect changes may prevent your device from booting.
Follow every step carefully.
:::

:::danger
ONLY MODIFY THE LINES SPECIFIED IN THIS GUIDE.
DO NOT EDIT OTHER FILES OR DIRECTORIES.
:::

---

## Create a GitHub Account

1. Go to [GitHub](https://github.com)


2. Create a **GitHub account** if you do not already have one.

---

## Fork the Repository

1. Open the repository containing the [**UEFI sources**](https://github.com/Project-Aloha/mu_aloha_platforms).
 > It should look something like this
 <img src="/InstallationGuides/Resources/OffTPM/0.png"/>
2. Click **Fork** in the top-right corner.
3. Wait until GitHub creates a copy of the repository in your account.

---

## Locate Your Device Files

1. Open your **forked repository**.
2. Find the folder with your {device codename}
 <img src="/InstallationGuides/Resources/OffTPM/1.png"/>
 <img src="/InstallationGuides/Resources/OffTPM/2.png"/>
3. Go back two steps in the directory
 <img src="/InstallationGuides/Resources/OffTPM/3.png"/>
4. Go to the **include** folder
 <img src="/InstallationGuides/Resources/OffTPM/4.png"/>
---

## Edit ACPI Configuration

1. Open the file:

```
acpi.inc
```

2. Find **line 19 and line 20**.

3. Add `#` before both lines.

- For Example:

>Before:

 <img src="/InstallationGuides/Resources/OffTPM/5.png"/>

> After:

 <img src="/InstallationGuides/Resources/OffTPM/6.png"/>

4. Click **Commit changes** to save the modification.

---

## Build UEFI Using GitHub Actions

1. Open the **Actions** tab in your repository.
2. Select the **build workflow**.
3. Run the workflow for your {**device codename**}.
4. Wait until the build finishes.

Download the compiled **UEFI image artifact** after the workflow completes.
---

## Boot the Modified UEFI

- Reboot your device to bootloader:

```
adb reboot bootloader
```

- Boot the compiled UEFI image.

> Replace `path\to\uefi.img` with the actual path:

```
fastboot boot path\to\uefi.img
```

---

# TPM is now disabled.

> If after this anything stops working for you, please contact the maintainer of your device.
