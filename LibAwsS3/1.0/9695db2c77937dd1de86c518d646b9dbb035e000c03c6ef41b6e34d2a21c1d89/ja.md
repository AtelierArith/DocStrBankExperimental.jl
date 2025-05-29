```
aws_s3_meta_request_acquire(meta_request)
```

参照を追加し、このオブジェクトを生存させます。参照は、使用が終わったときに解放する必要があります。さもなければ、そのメモリは決してクリーンアップされません。NULLを渡してはいけません。常に渡されたのと同じポインタを返します。

### プロトタイプ

```c
struct aws_s3_meta_request *aws_s3_meta_request_acquire(struct aws_s3_meta_request *meta_request);
```
