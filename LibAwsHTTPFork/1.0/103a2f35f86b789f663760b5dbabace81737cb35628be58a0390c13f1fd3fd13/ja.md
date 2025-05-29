```
aws_http2_stream_manager_acquire(manager)
```

ストリームマネージャから参照カウントを取得します。参照カウントがゼロに減少した後、ストリームマネージャは破棄を開始します。NULLは許容されます。newの後の初期参照カウントは1です。

# 引数

  * `manager`:

# 戻り値

取得した同じポインタ。

### プロトタイプ

```c
struct aws_http2_stream_manager *aws_http2_stream_manager_acquire(struct aws_http2_stream_manager *manager);
```
