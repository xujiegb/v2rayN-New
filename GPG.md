<a id="top"></a>

●
## GPG 

<div align="right">

▶ [中文](#中文) | [English](#english)

</div>

---

<a id="中文"></a>

#### 中文

## 使用 GPG (GnuPG) 验证你下载的 v2rayN 副本

### 说明

GnuPG，通常简称为 GPG，是 OpenPGP 标准的开源实现，可用于对文件进行签名和校验签名。对于 v2rayN 发布文件，GPG 校验可帮助确认下载文件是否由 2dust 的私钥签名，以及你下载的 v2rayN 公钥副本指纹是否与官方公布的指纹一致。同时还能确认文件在签名后是否被修改。

v2rayN 会在 GitHub Releases 中提供公钥和对应的 `.sig` 签名文件。校验发布文件时，请从同一个 Release 页面下载以下文件：

- 发布文件

```file
XXX
```

- 对应的 `.sig` 文件

```file
XXX.sig
```

- v2rayN 公钥文件

```file
v2rayN-public-key.asc
```

---

通用校验命令如下：

```bash
gpg --verify <signature-file.sig> <release-file>
```

例如：

```bash
gpg --verify v2rayN-windows-64.zip.sig v2rayN-windows-64.zip
```

> [!CAUTION]
> 如果公钥指纹与 README 中公布的指纹不一致，或 GPG 报告签名无效，请不要使用该下载文件。该文件可能不完整、被修改、被替换，或并非由预期发布密钥签名。如果仍然强行运行或安装，相关后果需自行承担，包括恶意软件感染、配置泄露、流量劫持或系统被入侵等风险。

---

### 安装 GPG

#### 先决条件

在安装 GnuPG 前，请确认满足以下条件：

- 你已经确认当前使用的操作系统范围受支持。
- 你有权限在当前系统中安装软件。
- 你可以在保存 v2rayN 下载文件的目录中打开 PowerShell 或终端。

#### Windows

从以下地址安装 Gpg4win：

```text
https://gpg4win.org/
```

安装完成后，在保存 v2rayN 下载文件的目录中打开 PowerShell。

---

#### macOS

从以下地址安装 GPG Suite：

```text
https://gpgtools.org/
```

安装完成后，在保存 v2rayN 下载文件的目录中打开终端。

---

#### Linux

##### RHEL / Fedora

使用以下命令安装 GnuPG：

```bash
sudo dnf install gnupg2
```

##### Ubuntu / Debian

使用以下命令安装 GnuPG：

```bash
sudo apt install gnupg
```

安装完成后，在保存 v2rayN 下载文件的目录中打开终端。

---

### 校验公钥

#### 先决条件

在校验公钥前，请确认满足以下条件：

- 你已经从 v2rayN 官方 GitHub Release 页面下载了公钥文件。

公钥文件名为：

```file
v2rayN-public-key.asc
```

- 你已经在系统中安装了 GnuPG。
- 你已确认项目 README 中公布的 v2rayN 公钥指纹。

从 GitHub Release 页面下载 v2rayN 公钥文件后，先查看该公钥文件的指纹：

```bash
gpg --show-keys --fingerprint v2rayN-public-key.asc
```

请将显示的公钥指纹与项目 README 中公布的指纹进行对比。确认一致后，再导入公钥：

```bash
gpg --import v2rayN-public-key.asc
```

> [!WARNING]
> 某些 GPG 版本可能只显示长指纹的前 50 位十六进制字符。如果显示出来的前 50 位十六进制字符与 README 中公布的指纹一致，这是正常情况，不必担心。

GPG 可能显示类似 `This key is not certified with a trusted signature` 的提示。这表示该公钥尚未在本机 GPG 信任数据库中被标记为可信，并不等于签名无效。关键步骤是手动核对公钥指纹是否与 README 中公布的指纹一致。

---

### 校验发布文件

#### 先决条件

在校验发布文件前，请确认满足以下条件：

- 你已经从同一个 v2rayN GitHub Release 页面下载了发布文件与对应的 `.sig` 签名文件。
- 你已经从官方 Release 页面下载并校验了 `v2rayN-public-key.asc`，且确认公钥指纹与 README 中公布的指纹一致。
- 你已经将该公钥导入到本机 GPG。

```file
XXX
XXX.sig
```

请确认发布文件和对应的 `.sig` 文件位于同一个目录。

使用以下命令格式：

```bash
gpg --verify <signature-file.sig> <release-file>
```

示例：

```bash
gpg --verify v2rayN-windows-64.zip.sig v2rayN-windows-64.zip
```

如果签名有效，GPG 会显示签名良好的信息。这表示该文件与签名匹配，并且在签名后没有被修改。

签名有效只表示该文件与已导入的公钥匹配。仍然必须确认已导入公钥的指纹与 README 中公布的指纹一致。

如果 GPG 报告签名错误、签名缺失、签名密钥不符合预期，或公钥指纹不一致，请删除下载文件，并从官方 GitHub Release 页面重新下载。

<div align="right">

[⬆ 返回顶部 / Back to top](#top) · [跳转到 English](#english)

</div>

---

<a id="english"></a>

#### English

## Verify your downloaded copy of v2rayN using GPG (GnuPG).

### Description

GnuPG, also known as GPG, is an open-source implementation of the OpenPGP standard. It can be used to sign files and verify signatures. For v2rayN Release files, GPG verification helps confirm the file was signed by 2dust's private key, that your downloaded v2rayN public key fingerprint matches the officially published one, and that the file wasn't modified after signing.

v2rayN provides the public key and the corresponding `.sig` signature files in GitHub Releases. To verify a Release file, download the following files from the same Release page:

- The release file

```file
XXX
```

- The corresponding `.sig` file

```file
XXX.sig
```

- The v2rayN public key

```file
v2rayN-public-key.asc
```

---

The general verification command is:

```bash
gpg --verify <signature-file.sig> <release-file>
```

For example:

```bash
gpg --verify v2rayN-windows-64.zip.sig v2rayN-windows-64.zip
```

> [!CAUTION]
> If the public key fingerprint does not match the fingerprint published in the README, or if GPG reports a bad signature, do not use the downloaded file. The file may be incomplete, modified, replaced, or not signed by the expected release key. If you still choose to run or install it, you are responsible for any resulting security risk, including malware infection, configuration theft, traffic interception, or system compromise.

---

### Install GPG

#### Prerequisites

Before installing GnuPG, make sure that the following conditions are met:

- You have confirmed that your operating system is supported.
- You have permission to install software on the current system.
- You can open PowerShell or Terminal in the directory containing the downloaded v2rayN files.

#### Windows

Install Gpg4win from:

```text
https://gpg4win.org/
```

After installation, open PowerShell in the directory containing the downloaded v2rayN files.

---

#### macOS

Install GPG Suite from:

```text
https://gpgtools.org/
```

After installation, open Terminal in the directory containing the downloaded v2rayN files.

---

#### Linux

##### RHEL / Fedora

Install GnuPG with:

```bash
sudo dnf install gnupg2
```

##### Ubuntu / Debian

Install GnuPG with:

```bash
sudo apt install gnupg
```

After installation, open Terminal in the directory containing the downloaded v2rayN files.

---

### Verify the public key

#### Prerequisites

Before verifying the public key, make sure that the following conditions are met:

- You have downloaded the public key file from the official v2rayN GitHub Release page.

The public key file is named:

```file
v2rayN-public-key.asc
```

- GnuPG is already installed on your system.
- You have confirmed the v2rayN public key fingerprint published in the project README.

After downloading the v2rayN public key from the GitHub Release page, display the fingerprint of the public key file:

```bash
gpg --show-keys --fingerprint v2rayN-public-key.asc
```

Compare the displayed fingerprint with the fingerprint published in the project README. After confirming that they match, import the public key:

```bash
gpg --import v2rayN-public-key.asc
```

> [!WARNING]
> Some GPG versions may display only the first 50 hexadecimal characters of a long fingerprint. If the displayed first 50 hexadecimal characters match the fingerprint published in the README, this is expected and does not indicate a problem.

GPG may show a message similar to `This key is not certified with a trusted signature`. This means the key has not been marked as trusted in your local GPG trust database. It does not automatically mean the signature is invalid. The important step is to manually compare the public key fingerprint with the fingerprint published in the README.

---

### Verify the release file

#### Prerequisites

Before verifying the Release file, make sure that the following conditions are met:

- You have downloaded the Release file and the corresponding `.sig` signature file from the same v2rayN GitHub Release page.
- You have downloaded and verified `v2rayN-public-key.asc` from the official Release page, and confirmed that the public key fingerprint matches the fingerprint published in the README.
- You have imported the public key into your local GPG keyring.

```file
XXX
XXX.sig
```

Make sure the release file and its `.sig` file are in the same directory.

Use the following command format:

```bash
gpg --verify <signature-file.sig> <release-file>
```

Example:

```bash
gpg --verify v2rayN-windows-64.zip.sig v2rayN-windows-64.zip
```

If the signature is valid, GPG prints a message indicating a good signature. This means the file matches the signature and has not been modified after it was signed.

A valid signature only proves that the file matches the imported public key. You must still verify that the imported public key fingerprint matches the fingerprint published in the README.

If GPG reports a bad signature, missing signature, unexpected key, or a fingerprint mismatch, delete the downloaded file and download it again from the official GitHub Release page.

<div align="right">

[⬆ Back to top](#top) · [跳转到中文 / Jump to Chinese](#中文)

</div>
