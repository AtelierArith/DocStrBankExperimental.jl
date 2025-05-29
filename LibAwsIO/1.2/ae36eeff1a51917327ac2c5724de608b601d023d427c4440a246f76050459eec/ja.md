```
aws_channel_release_hold(channel)
```

チャネルのメモリに対する保持を解除し、解放できるようにします。これは、[`aws_channel_destroy`](@ref)()の前または後に呼び出すことができます。

### プロトタイプ

```c
void aws_channel_release_hold(struct aws_channel *channel);
```
