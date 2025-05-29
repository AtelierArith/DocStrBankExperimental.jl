```
aws_s3_request_metrics_release(metrics)
```

参照を解放します。参照カウントが0に減少すると、このオブジェクトはクリーンアップされます。NULLを渡すことは問題ありません（何も起こりません）。常にNULLを返します。

### プロトタイプ

```c
struct aws_s3_request_metrics *aws_s3_request_metrics_release(struct aws_s3_request_metrics *metrics);
```
