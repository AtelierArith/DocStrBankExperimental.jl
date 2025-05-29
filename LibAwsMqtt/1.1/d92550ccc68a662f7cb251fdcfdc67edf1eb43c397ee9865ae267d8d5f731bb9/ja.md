```
aws_mqtt5_negotiated_settings_init(allocator, negotiated_settings, client_id)
```

交渉された設定内のクライアントIDバイトバッファを初期化します

# 引数

  * `allocator`: メモリ割り当てに使用するアロケータ
  * `negotiated_settings`: クライアントIDを適用する設定
  * `client_id`: 設定するクライアントID

### プロトタイプ

```c
int aws_mqtt5_negotiated_settings_init( struct aws_allocator *allocator, struct aws_mqtt5_negotiated_settings *negotiated_settings, const struct aws_byte_cursor *client_id);
```
