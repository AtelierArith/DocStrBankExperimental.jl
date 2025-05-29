```
Base.write(fp::S3Path, content::String; kwargs...)
Base.write(fp::S3Path, content::Vector{UInt8}; part_size_mb=50, multipart::Bool=true,
           returns::Symbol=:parsed, other_kwargs...,)
```

S3Path `fp` に `content` を書き込みます。

# オプション引数

  * `multipart`: `true` の場合、`part_size_mb` バイトを超える `content` のデータを [`s3_multipart_upload`](@ref) を介してアップロードします。`false` の場合、または `content` が `part_size_mb` より短い場合は、[`s3_put`](@ref) を介してデータをアップロードします。
  * `part_size_mb`: `multipart=true` の場合、分割されたデータの最大長（バイト単位）を設定します。
  * `returns`: 関数が返す結果を決定します：`:response`（AWS API の応答）、`:parsed`（デフォルト; 解析された AWS API の応答）、または `:path`（新しく作成された [`S3Path`](@ref）、バケットのバージョン管理が有効な場合はその `version` を含みます）。
  * `other_kwargs`: [`s3_multipart_upload`](@ref) に渡される追加の kwargs。
