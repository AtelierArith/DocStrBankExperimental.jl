フォロワー

このエンドポイントは、クライアントが持っているフォロワーのリストを取得することを可能にします。 "フォロワー"は、ウェブサイト上で他のユーザーをフォローしているユーザーです。 ページネーションをサポートしており、各ページにはデフォルトで80人のフォロワーが含まれます。

パラメータ:

  * page::Int64
  * per_page::Int64
  * sort::String

戻り値: Vector{GetFollowers200ResponseInner}, OpenAPI.Clients.ApiResponse
