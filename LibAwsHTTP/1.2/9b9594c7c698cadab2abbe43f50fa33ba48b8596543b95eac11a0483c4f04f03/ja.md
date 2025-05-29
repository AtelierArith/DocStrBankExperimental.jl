```
aws_http2_connection_change_settings(http2_connection, settings_array, num_settings, on_completed, user_data)
```

SETTINGSフレームを送信します（HTTP/2のみ）。SETTINGSは、ピアからSETTINGS ACKを受信したときにローカルに適用されます。

# 引数

  * `http2_connection`: HTTP/2接続。
  * `settings_array`: 変更する設定の配列。注意：各設定にはその境界があります。
  * `num_settings`: settings_arrayで変更する設定の数。
  * `on_completed`: オプションのコールバック、[`aws_http2_on_change_settings_complete_fn`](@ref)を参照してください。
  * `user_data`: on_completedコールバックに渡すユーザーデータ。

### プロトタイプ

```c
int aws_http2_connection_change_settings( struct aws_http_connection *http2_connection, const struct aws_http2_setting *settings_array, size_t num_settings, aws_http2_on_change_settings_complete_fn *on_completed, void *user_data);
```
