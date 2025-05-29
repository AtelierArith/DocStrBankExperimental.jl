```
aws_http2_stream_manager_release(manager)
```

ストリームマネージャーから参照カウントを解放します。参照カウントがゼロに減少した後、ストリームマネージャーは破棄を開始します。NULLは許容されます。newの後の初期参照カウントは1です。

# 引数

  * `manager`:

# 戻り値

NULL

### プロトタイプ

```c
struct aws_http2_stream_manager *aws_http2_stream_manager_release(struct aws_http2_stream_manager *manager);
```
