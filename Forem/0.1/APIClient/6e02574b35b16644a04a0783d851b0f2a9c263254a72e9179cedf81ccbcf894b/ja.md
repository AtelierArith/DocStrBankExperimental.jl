公開された記事のパスによる取得

このエンドポイントは、クライアントがその `path` に基づいて単一の公開された記事を取得できるようにします。

パラメータ:

  * username::String (必須)
  * slug::String (必須)

返却: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
