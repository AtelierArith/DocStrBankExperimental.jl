```
Base.write(fp::S3Path, content::String; kwargs...)
Base.write(fp::S3Path, content::Vector{UInt8}; part_size_mb=50, multipart::Bool=true,
           returns::Symbol=:parsed, other_kwargs...,)
```

Write `content` to S3Path `fp`.

# Optional Arguments

  * `multipart`: when `true`, uploads data via [`s3_multipart_upload`](@ref) for `content` greater than `part_size_mb` bytes; when false, or when `content` is shorter than `part_size_mb`, uploads data via [`s3_put`](@ref).
  * `part_size_mb`: when `multipart=true`, sets maximum length of partitioned data (in bytes).
  * `returns`: determines the result returned by the function: `:response` (the AWS API response), :parsed`(default; the parsed AWS API response), or`:path`(the newly created [`S3Path`](@ref), including its`version` when versioning is enabled for the bucket).
  * `other_kwargs`: additional kwargs passed through into [`s3_multipart_upload`](@ref).
