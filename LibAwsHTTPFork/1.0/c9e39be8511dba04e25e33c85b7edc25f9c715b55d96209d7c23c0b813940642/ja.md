```
aws_websocket_is_data_frame(opcode)
```

オペコードがデータフレームの場合はtrueを返し、オペコードが制御フレームの場合はfalseを返します。

### プロトタイプ

```c
bool aws_websocket_is_data_frame(uint8_t opcode);
```
