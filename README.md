
readme_content = """# Android 压力测试工具

一款基于 Kotlin + Coroutines + OkHttp 的高并发 HTTP/HTTPS 压力测试 Android 应用。

## 功能特性

- **高并发测试**：支持 1-1000 并发线程，模拟真实高负载场景
- **实时统计**：实时显示 QPS、成功率、平均/最大/最小响应时间
- **灵活配置**：可设置目标 URL、并发数、测试持续时间
- **结果导出**：支持将测试结果导出为 CSV 文件到手机 Download 目录
- **测试控制**：支持开始、暂停、继续、停止测试操作
- **屏幕旋转保护**：测试过程中旋转屏幕不丢失状态

## 技术栈

| 技术 | 版本 |
|------|------|
| compileSdk | 35 (Android 15) |
| minSdk | 24 (Android 7.0) |
| targetSdk | 35 |
| JDK | 21 |
| Kotlin | 2.0+ |
| OkHttp | 4.12.0 |
| Kotlin Coroutines | 1.10.x |
| Material Design 3 | 最新稳定版 |
| MVVM 架构 | ViewModel + Repository |

## 项目结构

```
stress-test-app/
├── .github/workflows/     # GitHub Actions CI/CD 配置
├── app/
│   ├── src/main/
│   │   ├── java/com/example/stresstest/
│   │   │   ├── MainActivity.kt          # 主界面
│   │   │   ├── StressTestViewModel.kt   # 业务逻辑
│   │   │   ├── StressTestRepository.kt  # 数据层/网络请求
│   │   │   └── StressTestResult.kt      # 数据模型
│   │   └── res/
│   │       ├── layout/activity_main.xml # 主界面布局
│   │       └── values/                  # 颜色、字符串、主题
│   └── build.gradle.kts               # 模块级构建配置
├── build.gradle.kts                   # 项目级构建配置
├── settings.gradle.kts                # 项目设置
├── gradle.properties                  # Gradle 属性
└── gradlew / gradlew.bat              # Gradle Wrapper
```

## 本地开发环境

### 系统要求
- Linux 系统（无图形界面支持）
- Git 2.47+
- OpenJDK 21
- Vim/Nano 编辑器

### 已验证环境
```
Git: 2.47.3
Vim: 9.1
cURL: 8.14.1
OpenJDK: 21.0.11
系统: Debian trixie
```

## 构建方式

### 方式一：GitHub Actions 云编译（推荐）

1. 推送代码到 `main` 分支
2. GitHub Actions 自动编译并发布 Release
3. 从 [Releases 页面](../../releases) 下载 APK

### 方式二：本地命令行编译

```bash
# 克隆仓库
git clone https://github.com/mohuanmo/stress-test-app.git
cd stress-test-app

# 确保 Gradle Wrapper 可执行
chmod +x gradlew

# 编译 Debug APK
./gradlew assembleDebug

# APK 输出路径
# app/build/outputs/apk/debug/app-debug.apk
```

## 使用说明

1. 安装 APK 到 Android 设备
2. 打开应用，输入目标 URL
3. 设置并发线程数（1-1000）和测试持续时间（秒）
4. 点击"开始测试"
5. 实时查看 QPS、成功率、响应时间等统计
6. 测试结束后可导出 CSV 报告

## CI/CD 配置

本项目使用 GitHub Actions 自动编译：

- **触发条件**：push 到 `main` 分支 或 手动触发
- **运行环境**：ubuntu-latest
- **JDK**：Temurin 21
- **编译命令**：`./gradlew assembleDebug`
- **产物**：自动创建 Release 并上传 APK

## 权限说明

应用需要以下权限：
- `INTERNET`：网络请求
- `WRITE_EXTERNAL_STORAGE`：导出 CSV 到 Download 目录（Android 10+ 使用 MediaStore）

## 开源协议

MIT License

## 作者

[mohuanmo](https://github.com/mohuanmo)
