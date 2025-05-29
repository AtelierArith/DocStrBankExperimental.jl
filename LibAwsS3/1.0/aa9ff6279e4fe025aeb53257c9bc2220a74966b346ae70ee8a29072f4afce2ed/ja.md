```
aws_s3_meta_request_release(meta_request)
```

参照を解放します。参照カウントが0に減少すると、このオブジェクトはクリーンアップされます。NULLを渡すことは問題ありません（何も起こりません）。常にNULLを返します。

### プロトタイプ

```c
struct aws_s3_meta_request *aws_s3_meta_request_release(struct aws_s3_meta_request *meta_request);
```
