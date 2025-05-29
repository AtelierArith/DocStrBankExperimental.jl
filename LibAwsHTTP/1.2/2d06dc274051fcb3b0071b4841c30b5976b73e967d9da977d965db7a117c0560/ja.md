```
aws_http2_connection_get_local_settings(http2_connection, out_settings)
```

デコーディングに影響を与えるために使用しているローカル設定を取得します。

# 引数

  * `http2_connection`: HTTP/2 接続。
  * `out_settings`: ローカル設定に設定される [`aws_http2_setting`](@ref) の固定サイズ配列

### プロトタイプ

```c
void aws_http2_connection_get_local_settings( const struct aws_http_connection *http2_connection, struct aws_http2_setting out_settings[AWS_HTTP2_SETTINGS_COUNT]);
```
