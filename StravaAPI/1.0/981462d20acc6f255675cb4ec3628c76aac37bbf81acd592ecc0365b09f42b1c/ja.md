アクティビティを取得

認証されたアスリートが所有する指定されたアクティビティを返します。EveryoneおよびFollowersアクティビティにはactivity:readが必要です。Only Meアクティビティにはactivity:read_allが必要です。

パラメータ:

  * id::Int64 (必須)
  * include*all*efforts::Bool

返却: DetailedActivity, OpenAPI.Clients.ApiResponse
