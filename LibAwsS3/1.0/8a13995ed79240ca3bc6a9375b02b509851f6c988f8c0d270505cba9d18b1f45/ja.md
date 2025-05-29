```
aws_s3_meta_request_resume_token_new_upload(allocator, options)
```

永続化されたデータからアップロード再開トークンを作成します。注意: 再開トークンに必要なデータは操作ごとに異なります。

### プロトタイプ

```c
struct aws_s3_meta_request_resume_token *aws_s3_meta_request_resume_token_new_upload( struct aws_allocator *allocator, const struct aws_s3_upload_resume_token_options *options);
```
