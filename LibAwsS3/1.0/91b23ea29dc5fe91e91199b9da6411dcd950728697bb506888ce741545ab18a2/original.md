```
aws_s3_endpoint_resolver_new(allocator)
```

Creates a new S3 endpoint resolver. Warning: Before using this header, you have to enable it by setting cmake config AWS_ENABLE_S3_ENDPOINT_RESOLVER=ON

### Prototype

```c
struct aws_endpoints_rule_engine *aws_s3_endpoint_resolver_new(struct aws_allocator *allocator);
```
