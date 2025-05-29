```
aws_s3_library_init(allocator)
```

aws-c-s3で使用される内部データ構造を初期化します。aws-c-s3の機能を使用する前に呼び出す必要があります。

### プロトタイプ

```c
void aws_s3_library_init(struct aws_allocator *allocator);
```
