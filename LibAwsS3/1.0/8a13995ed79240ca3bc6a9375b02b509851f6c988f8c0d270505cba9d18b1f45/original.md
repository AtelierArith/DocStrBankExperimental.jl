```
aws_s3_meta_request_resume_token_new_upload(allocator, options)
```

Create upload resume token from persisted data. Note: Data required for resume token varies per operation.

### Prototype

```c
struct aws_s3_meta_request_resume_token *aws_s3_meta_request_resume_token_new_upload( struct aws_allocator *allocator, const struct aws_s3_upload_resume_token_options *options);
```
