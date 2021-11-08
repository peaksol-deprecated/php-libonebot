# php-libonebot

PHP 的 LibOneBot 库。LibOneBot 可以帮助 OneBot 实现者快速在新的聊天机器人平台实现 OneBot v12 接口标准。

基于 LibOneBot 实现 OneBot 时，OneBot 实现者只需专注于编写与聊天机器人平台对接的逻辑，包括通过长轮询或 webhook 方式从机器人平台获得事件，并将其转换为 OneBot 事件，以及处理 OneBot 动作请求，并将其转换为对机器人平台 API 的调用。

**当前版本还在开发中，在发布正式版之前此库内的接口可能会发生较大变动。**

更新日志：<docs/update.md>

## 使用

```shell
composer require onebot/libonebot
```

## 尝试 demo

在 require 下载 libob 库后，新建文件 `demo.php` 和 `demo.json`，并在 `demo.php` 中写如下代码：

```php
<?php

require_once "vendor/autoload.php";

$ob = new \OneBot\V12\OneBot("repl", "qq");
$ob->setServerDriver(new \OneBot\V12\Driver\WorkermanDriver(), new \OneBot\V12\Driver\Config\WorkermanConfig("demo.json"));
$ob->setActionHandler(\OneBot\V12\Action\ReplAction::class);
$ob->run();
```

此 demo 以一个命令行交互的方式使用 LibOneBot 快速完成了一个 OneBot 实现，命令行中输入内容即可发送到 OneBot，使用 HTTP 或 WebSocket 发送给 LibOneBot 后可以将信息显示在终端内。

```bash
# 运行 OneBot 实现
php demo.php
```