```
aws_s3_client_release(client)
```

参照を解放します。参照カウントが0に減少すると、このオブジェクトはクリーンアップされます。NULLを渡すことは問題ありません（何も起こりません）。常にNULLを返します。

### プロトタイプ

```c
struct aws_s3_client *aws_s3_client_release(struct aws_s3_client *client);
```
