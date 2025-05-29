```
ls(; type="block", api::PrefectAPI = PrefectAPI())
```

Prefectサーバーを呼び出し、定義されたすべてのブロックのリストをVector{String}として返します。デフォルトではすべてのブロックをリストしますが、後の実装では「フロー」、「デプロイメント」、「ワークプール」などが含まれる可能性があります。必要に応じて認証に関する詳細は`PrefectAPI`のドキュメントを参照してください。

# 例:

```julia
julia> ENV["PREFECT_API_URL"] = "http://127.0.0.1:4300/api";

julia> ls()
11-element Vector{Any}:
 "aws-credentials/subdivisions"
 "docker-container/lamneth"
 "github/dev"
 "github/main"
 "local-file-system/willowdata"
 "process/red-barchetta"
 "s3/necromancer"
 "s3-bucket/willowdata"
 "secret/necromancer"
 "slack-webhook/bytor-alert"
 "string/environment"
```
