アクティビティゾーンを取得

Summit機能。指定されたアクティビティのゾーンを返します。EveryoneおよびFollowersアクティビティにはactivity:readが必要です。Only Meアクティビティにはactivity:read_allが必要です。

パラメータ:

  * id::Int64 (必須)

返り値: Vector{ActivityZone}, OpenAPI.Clients.ApiResponse
