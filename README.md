# aasa-test

✅ 一、前提准备

你需要：

    一个 GitHub 账号（注册免费）

    一个 Flutter App 的 iOS Bundle ID（如：com.example.myapp）

    Apple Developer Team ID（如：ABCDE12345）

✅ 二、生成 AASA 文件
🧩 文件内容模板：

{
  "applinks": {
    "apps": [],
    "details": [
      {
        "appID": "ABCDE12345.com.example.myapp",
        "paths": [ "/app/*" ]
      }
    ]
  }
}

替换：

    ABCDE12345：你的 Apple Team ID

    com.example.myapp：你的 App 的 Bundle ID

保存为文件名：

apple-app-site-association  （注意：没有 `.json` 后缀）

✅ 三、部署到 GitHub Pages
🧩 步骤 1：新建仓库

    名称如：aasa-host

    设为 Public（公开）

    勾选 Initialize this repository with a README

🧩 步骤 2：上传 AASA 文件

在仓库根目录创建 .well-known 目录：

.well-known/apple-app-site-association

你可以在本地这样操作后上传：

mkdir .well-known
mv apple-app-site-association .well-known/

使用 Git 客户端上传或网页上传皆可。
🧩 步骤 3：启用 GitHub Pages

    进入仓库 → Settings → Pages

    在 “Source” 下拉中选择：

Deploy from a branch
Branch: main (or master)
Folder: / (root)

    保存，几秒后会看到生成的链接，比如：

https://yourgithubusername.github.io/aasa-host/

✅ 四、最终访问路径

AASA 文件应访问于：

https://yourgithubusername.github.io/aasa-host/.well-known/apple-app-site-association

这个路径可以作为微信开放平台中配置的 Universal Link 的前缀，如：

https://yourgithubusername.github.io/aasa-host/app/

✅ 五、微信开放平台配置示例
字段	示例
Universal Link	https://yourgithubusername.github.io/aasa-host/app/
AppID	与 Apple Developer 中注册的 AppID 一致
✅ 测试是否成功

访问：

https://yourgithubusername.github.io/aasa-host/.well-known/apple-app-site-association

    ✅ 如果直接显示 JSON，则成功

    ❌ 如果返回 404，检查文件路径、扩展名、目录是否正确

🧠 注意事项
项目	说明
必须 HTTPS	GitHub Pages 默认提供
Content-Type	GitHub 会自动识别为 application/json，无需设置
不能带 .json 扩展名	文件名必须精确为 apple-app-site-association
不能重定向	GitHub Pages 原生支持，无跳转问题