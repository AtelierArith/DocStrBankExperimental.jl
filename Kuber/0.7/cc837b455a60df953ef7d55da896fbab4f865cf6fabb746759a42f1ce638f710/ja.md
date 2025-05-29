```
set_server(ctx, uri, reset_api_versions=false; max_tries=5, kwargs...)
```

Kubernetes APIサーバーエンドポイントをコンテキストに設定します。

引数:

  * ctx: APIサーバーエンドポイントを設定するコンテキスト
  * uri: APIサーバーエンドポイントのURI
  * reset*api*versions: サーバーがサポートするAPIバージョンを再度調査するかどうか（デフォルトはfalse）

キーワード引数:

  * max_tries: サーバーからAPIバージョンを調査する際に許可される再試行回数
  * verbose: APIバージョンをログに記録
  * kwargs: APIサーバーのクライアントを構築する際に渡す他のキーワード引数（OpenAPI.jlを参照 - https://github.com/JuliaComputing/OpenAPI.jl#readme）
