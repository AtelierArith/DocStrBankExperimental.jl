```
aws_websocket_acquire(websocket)
```

ウェブソケットの参照カウントを増加させ、破棄されるのを防ぎます。

# 戻り値

常に渡されたのと同じポインタを返します。

### プロトタイプ

```c
struct aws_websocket *aws_websocket_acquire(struct aws_websocket *websocket);
```
