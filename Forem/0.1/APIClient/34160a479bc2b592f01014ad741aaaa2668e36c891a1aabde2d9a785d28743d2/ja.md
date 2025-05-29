組織のアーティクル

このエンドポイントは、クライアントが組織に属するアーティクルのリストを取得することを可能にします。ページネーションをサポートしており、各ページにはデフォルトで `30` ユーザーが含まれます。

パラメータ:

  * username::String (必須)
  * page::Int64
  * per_page::Int64

戻り値: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
