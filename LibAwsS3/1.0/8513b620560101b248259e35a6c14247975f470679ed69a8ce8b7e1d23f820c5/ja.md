```
aws_s3_request_metrics_acquire(metrics)
```

参照を追加し、このオブジェクトを生存させます。参照は、使用が終わったときに解放する必要があります。さもなければ、そのメモリは決してクリーンアップされません。常に渡されたのと同じポインタを返します。

### プロトタイプ

```c
struct aws_s3_request_metrics *aws_s3_request_metrics_acquire(struct aws_s3_request_metrics *metrics);
```
