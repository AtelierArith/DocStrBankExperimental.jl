```
testing_channel_increment_read_window(testing, size)
```

ダウンストリームハンドラーにウィンドウ更新を発行させたい場合

### プロトタイプ

```c
static inline int testing_channel_increment_read_window(struct testing_channel *testing, size_t size);
```
