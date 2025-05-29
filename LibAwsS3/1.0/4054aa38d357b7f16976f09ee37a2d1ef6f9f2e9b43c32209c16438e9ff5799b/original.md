```
aws_s3_request_type_operation_name(type)
```

Return operation name for [`aws_s3_request_type`](@ref), or empty string if the type doesn't map to an actual operation. For example: AWS_S3_REQUEST_TYPE_HEAD_OBJECT -> "HeadObject" AWS_S3_REQUEST_TYPE_UNKNOWN -> "" AWS_S3_REQUEST_TYPE_MAX -> ""

### Prototype

```c
const char *aws_s3_request_type_operation_name(enum aws_s3_request_type type);
```
