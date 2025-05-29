```
aws_channel_acquire_hold(channel)
```

チャネルのメモリが解放されるのを防ぎます。任意の数のユーザーがチャネルとそのハンドラーが予期せず解放されるのを防ぐためにホールドを取得できます。ホールドを取得したユーザーは、[`aws_channel_release_hold`](@ref)()を介してそれを解放する必要があります。すべてのホールドが解放され、[`aws_channel_destroy`](@ref)()が呼び出されると、メモリは解放されます。

### プロトタイプ

```c
void aws_channel_acquire_hold(struct aws_channel *channel);
```
