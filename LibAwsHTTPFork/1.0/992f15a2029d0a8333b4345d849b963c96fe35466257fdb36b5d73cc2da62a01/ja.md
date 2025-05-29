```
aws_websocket_send_frame(websocket, options)
```

ウェブソケットフレームを送信します。`options`構造体はコピーされます。操作が完了するとコールバックが呼び出されます。この関数は任意のスレッドから呼び出すことができます。

### プロトタイプ

```c
int aws_websocket_send_frame(struct aws_websocket *websocket, const struct aws_websocket_send_frame_options *options);
```
