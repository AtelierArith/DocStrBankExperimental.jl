アクティビティラップのリスト

識別子によって特定されたアクティビティのラップを返します。EveryoneおよびFollowersアクティビティにはactivity:readが必要です。Only Meアクティビティにはactivity:read_allが必要です。

パラメータ:

  * id::Int64 (必須)

返却: Vector{Lap}, OpenAPI.Clients.ApiResponse
