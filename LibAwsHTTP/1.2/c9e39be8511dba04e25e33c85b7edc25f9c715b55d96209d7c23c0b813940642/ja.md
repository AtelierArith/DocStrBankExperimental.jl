```
aws_websocket_is_data_frame(opcode)
```

opcodeがデータフレームの場合はtrueを返し、opcodeが制御フレームの場合はfalseを返します。

### プロトタイプ

```c
bool aws_websocket_is_data_frame(uint8_t opcode);
```
