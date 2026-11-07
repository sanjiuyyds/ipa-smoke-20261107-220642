# Smoke220642

用 GitHub Actions 编译、本地证书自签的 iOS 工程。

## 目录

```
Smoke220642/                        源码
Smoke220642.xcodeproj/              Xcode 工程（手写 pbxproj，无 Mac 也能维护）
.github/workflows/build.yml        CI 定义
```

## 首次使用

```bash
git init
git branch -M main
git remote add origin https://github.com/<YOU>/ipa-smoke-20261107-220642.git
git add -A
git commit -m "init"
git push -u origin main
```

然后去 GitHub Actions 页面手动 Run workflow，或：
```bash
curl -X POST -H "Authorization: Bearer <TOKEN>" \
  -H "Accept: application/vnd.github+json" \
  https://api.github.com/repos/<YOU>/ipa-smoke-20261107-220642/actions/workflows/build.yml/dispatches \
  -d '{"ref":"main"}'
```

## 本地编译为什么不行

`xcodebuild` 只能在 macOS 上跑。Windows/Linux 上没有 iOS SDK 的 clang 驱动，
zig 的 Apple target 也必须 macOS 主机。

## 签名

CI 产出的 ipa **未签名**。用 i4Tools / 全能签 / Sideloadly 用你自己的证书重签后安装。

## 详细文档

见 `docs/IOS-BUILD-GUIDE-UNIVERSAL.md`
