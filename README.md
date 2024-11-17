# 适配多操作系统的【文件选择器（模态）对话框】与【通知消息（模态）对话框】

## `Fork`分支的独有贡献

相较于`Origin`分支，我尤其解决了`rfd`在`MacOS`操作系统内，从`cocoa`的`appKit`上下文外（包括“事件循环”与“主窗体”），凭空弹出`NSAlert`消息对话框不能自动收起的缺陷。比如，从命令行上下文（在这，既没事件循环，更无主窗体）弹出的【通知消息（模态）对话框】，在点击`OK`按钮后，无法自动收起且进入无响应状态。我是在给公司技术团队制作生产力工具过程中遇到此问题 — 伤害性不大，恶心度很高。这么一比还是`Win32`的`COM ABI`更好用，没那么多技术细节的坑要踩。希望华为鸿蒙的`N-API`或`NDK`应用程序二进制接口不会出现类似的坑。

### 修复后效果

点击按钮之后，【通知消息（模态）对话框】真的会被折叠收起。

![rfd-修复成果](https://github.com/user-attachments/assets/6585399b-74f6-4c38-bf1e-4bea445b3c7f)

## 其它简介

![img](https://github.com/PolyMeilex/rfd/assets/20758186/9bef59fa-60f0-448c-b9db-44ab436ee611)

[![version](https://img.shields.io/crates/v/rfd.svg)](https://crates.io/crates/rfd)
[![Documentation](https://docs.rs/rfd/badge.svg)](https://docs.rs/rfd)
[![dependency status](https://deps.rs/crate/rfd/0.15.1/status.svg)](https://deps.rs/crate/rfd/0.15.1)

Rusty File Dialogs is a cross platform Rust library for using native file open/save dialogs.
It provides both asynchronous and synchronous APIs. Supported platforms:

* Windows
* macOS
* Linux & BSDs (GTK3 or XDG Desktop Portal)
* WASM32 (async only)

Refer to the [documentation](https://docs.rs/rfd) for more details.

## Platform-specific notes

### Linux

Please refer to [Linux & BSD backends](https://docs.rs/rfd/latest/rfd/#linux--bsd-backends) for information about the needed dependencies to be able to compile on Linux.
