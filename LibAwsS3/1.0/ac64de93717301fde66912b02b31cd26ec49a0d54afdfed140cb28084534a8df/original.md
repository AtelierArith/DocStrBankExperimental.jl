```
aws_s3_meta_request_type
```

A Meta Request represents a group of generated requests that are being done on behalf of the original request. For example, one large GetObject request can be transformed into a series of ranged GetObject requests that are executed in parallel to improve throughput.

The [`aws_s3_meta_request_type`](@ref) is a hint of transformation to be applied.
