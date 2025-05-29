```
aws_http2_connection_get_remote_settings(http2_connection, out_settings)
```

リモートピアから受信した設定を取得します。これは、送信するメッセージを制限するために使用されます。

# 引数

  * `http2_connection`: HTTP/2 接続。
  * `out_settings`: リモート設定に設定される [`aws_http2_setting`](@ref) の固定サイズ配列

### プロトタイプ

```c
void aws_http2_connection_get_remote_settings( const struct aws_http_connection *http2_connection, struct aws_http2_setting out_settings[AWS_HTTP2_SETTINGS_COUNT]);
```
