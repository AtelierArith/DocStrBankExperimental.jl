```
aws_s3_request_type
```

The type of a single S3 HTTP request. Used by metrics. A meta-request can make multiple S3 HTTP requests under the hood.

For example, AWS_S3_META_REQUEST_TYPE_PUT_OBJECT for a large file will do multipart upload, resulting in 3+ HTTP requests: AWS_S3_REQUEST_TYPE_CREATE_MULTIPART_UPLOAD, one or more AWS_S3_REQUEST_TYPE_UPLOAD_PART, and finally AWS_S3_REQUEST_TYPE_COMPLETE_MULTIPART_UPLOAD.

[`aws_s3_request_type_operation_name`](@ref)() returns the S3 operation name for types that map (e.g. AWS_S3_REQUEST_TYPE_HEAD_OBJECT -> "HeadObject"), or empty string for types that don't map (e.g. AWS_S3_REQUEST_TYPE_UNKNOWN -> "").
