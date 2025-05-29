アクティビティのKudoerをリストします

識別子によって特定されたアクティビティにKudoしたアスリートを返します。EveryoneおよびFollowersアクティビティにはactivity:readが必要です。Only Meアクティビティにはactivity:read_allが必要です。

パラメータ:

  * id::Int64 (必須)
  * page::Int64
  * per_page::Int64

返り値: Vector{SummaryAthlete}, OpenAPI.Clients.ApiResponse
