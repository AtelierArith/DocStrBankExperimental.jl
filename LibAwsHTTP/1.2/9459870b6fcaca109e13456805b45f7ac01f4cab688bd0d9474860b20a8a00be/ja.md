```
aws_http2_stream_manager_acquire_stream(http2_stream_manager, acquire_stream_option)
```

ストリームマネージャからストリームを非同期に取得します。

# 引数

  * `http2_stream_manager`:
  * `acquire_stream_option`: [`aws_http2_stream_manager_acquire_stream_options`](@ref)を参照

### プロトタイプ

```c
void aws_http2_stream_manager_acquire_stream( struct aws_http2_stream_manager *http2_stream_manager, const struct aws_http2_stream_manager_acquire_stream_options *acquire_stream_option);
```
