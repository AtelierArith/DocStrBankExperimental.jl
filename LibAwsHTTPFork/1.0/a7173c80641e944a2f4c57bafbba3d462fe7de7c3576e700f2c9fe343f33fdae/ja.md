```
aws_websocket_close(websocket, free_scarce_resources_immediately)
```

ウェブソケット接続を閉じます。接続がすでに閉じているか、閉じつつある場合でも、この呼び出しは安全です。ウェブソケットは、通常のシャットダウン中にCLOSEフレームを送信しようとします。`free_scarce_resources_immediately`がtrueの場合、接続はできるだけ早く切断されます。この関数は任意のスレッドから呼び出すことができます。

### プロトタイプ

```c
void aws_websocket_close(struct aws_websocket *websocket, bool free_scarce_resources_immediately);
```
