更新アクティビティ

認証されたアスリートが所有する指定されたアクティビティを更新します。activity:writeが必要です。また、Only Meアクティビティを更新するためにはactivity:read_allも必要です。

パラメータ:

  * id::Int64 (必須)
  * body::UpdatableActivity

戻り値: DetailedActivity, OpenAPI.Clients.ApiResponse
