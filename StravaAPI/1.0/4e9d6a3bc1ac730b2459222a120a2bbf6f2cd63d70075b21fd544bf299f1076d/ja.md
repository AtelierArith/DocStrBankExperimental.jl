リストアクティビティコメント

指定されたアクティビティに対するコメントを返します。EveryoneおよびFollowersアクティビティにはactivity:readが必要です。Only Meアクティビティにはactivity:read_allが必要です。

パラメータ:

  * id::Int64 (必須)
  * page::Int64
  * per_page::Int64
  * page_size::Int64
  * after_cursor::String

返却: Vector{Comment}, OpenAPI.Clients.ApiResponse
