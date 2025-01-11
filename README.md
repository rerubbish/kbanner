# kbanner

「没啥用出品，必是没啥用」![Maven Central Version](https://img.shields.io/maven-central/v/io.github.rerubbish/kbanner)

此插件用于 ktor 框架，在启动时打印 banner，类似 Spring 框架在启动时打印 banner 的效果。

## 使用

依赖引用

Gradle Kotlin DSL

```kts
implementation("io.github.rerubbish:kbanner:0.1.0")
```

Maven

```xml
<dependency>
    <groupId>io.github.rerubbish</groupId>
    <artifactId>kbanner</artifactId>
    <version>0.1.0</version>
</dependency>
```

代码中使用插件

```kotlin
fun main() {
    embeddedServer(
        Netty,
        port = 8080,
        host = "0.0.0.0",
        module = {
            install(KBanner)
        }
    ).start(wait = true)
}
```

也可自定义banner，在资源目录下创建`banner.txt`文件，这样不需要配置插件，会默认读取该文件。

或者在资源目录下创建文件`我佛慈悲庇佑世间无永无bug.txt`，再在插件中配置上相对资源目录的路径即可。

```kotlin
fun main() {
    embeddedServer(
        Netty,
        port = 8080,
        host = "0.0.0.0",
        module = {
            install(KBanner) {
                location = "我佛慈悲庇佑世间无永无bug.txt"
            }
        }
    ).start(wait = true)
}
```
