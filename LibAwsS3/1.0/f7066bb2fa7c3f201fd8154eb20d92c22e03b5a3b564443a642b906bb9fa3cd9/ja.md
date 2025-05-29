```
aws_s3_request_type
```

単一のS3 HTTPリクエストのタイプ。メトリクスによって使用されます。メタリクエストは、内部で複数のS3 HTTPリクエストを行うことができます。

例えば、大きなファイルのためのAWS*S3*META*REQUEST*TYPE*PUT*OBJECTは、マルチパートアップロードを行い、3つ以上のHTTPリクエストを生成します：AWS*S3*REQUEST*TYPE*CREATE*MULTIPART*UPLOAD、1つ以上のAWS*S3*REQUEST*TYPE*UPLOAD*PART、そして最終的にAWS*S3*REQUEST*TYPE*COMPLETE*MULTIPART_UPLOAD。

[`aws_s3_request_type_operation_name`](@ref)()は、マッピングされるタイプのS3操作名を返します（例：AWS*S3*REQUEST*TYPE*HEAD*OBJECT -> "HeadObject"）、またはマッピングされないタイプの場合は空の文字列を返します（例：AWS*S3*REQUEST*TYPE_UNKNOWN -> ""）。
