Readinglist

このエンドポイントは、クライアントがユーザーのリーディングリストに保存された記事のリストを取得できるようにします。デフォルトでは、各ページには `30` 記事が含まれ、ページネーションをサポートしています。

パラメータ:

  * page::Int64
  * per_page::Int64

戻り値: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
