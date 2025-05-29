```
aws_s3_request_type_operation_name(type)
```

[`aws_s3_request_type`](@ref)の操作名を返します。タイプが実際の操作にマッピングされていない場合は空の文字列を返します。例えば: AWS*S3*REQUEST*TYPE*HEAD*OBJECT -> "HeadObject" AWS*S3*REQUEST*TYPE*UNKNOWN -> "" AWS*S3*REQUEST*TYPE_MAX -> ""

### プロトタイプ

```c
const char *aws_s3_request_type_operation_name(enum aws_s3_request_type type);
```
