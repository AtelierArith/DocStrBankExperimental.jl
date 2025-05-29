```
aws_s3_client_acquire(client)
```

このオブジェクトを生かしておくために参照を追加します。参照は、使用が終わったら解放しなければなりません。さもなければ、そのメモリは決してクリーンアップされません。NULLを渡してはいけません。常に渡されたのと同じポインタを返します。

### プロトタイプ

```c
struct aws_s3_client *aws_s3_client_acquire(struct aws_s3_client *client);
```
