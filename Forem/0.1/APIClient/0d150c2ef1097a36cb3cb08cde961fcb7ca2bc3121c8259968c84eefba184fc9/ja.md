公開された記事

このエンドポイントは、クライアントが記事のリストを取得できるようにします。「記事」とは、ユーザーがDEV上で作成するすべての投稿であり、通常はフィードに表示されます。これらはブログ投稿、ディスカッションの質問、ヘルプスレッドなどである可能性がありますが、コード内では記事として参照されます。デフォルトでは、人気の降順でフィーチャーされた公開記事が返されます。ページネーションをサポートしており、各ページにはデフォルトで`30`の記事が含まれます。

パラメータ:

  * page::Int64
  * per_page::Int64
  * tag::String
  * tags::String
  * tags_exclude::String
  * username::String
  * state::String
  * top::Int64
  * collection_id::Int64

返り値: Vector{ArticleIndex}, OpenAPI.Clients.ApiResponse
