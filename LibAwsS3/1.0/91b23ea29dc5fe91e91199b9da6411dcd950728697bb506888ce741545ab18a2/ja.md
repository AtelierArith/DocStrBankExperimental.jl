```
aws_s3_endpoint_resolver_new(allocator)
```

新しい S3 エンドポイントリゾルバーを作成します。警告: このヘッダーを使用する前に、cmake 設定 AWS*ENABLE*S3*ENDPOINT*RESOLVER=ON を設定して有効にする必要があります。

### プロトタイプ

```c
struct aws_endpoints_rule_engine *aws_s3_endpoint_resolver_new(struct aws_allocator *allocator);
```
