アクティビティストリームを取得

指定されたアクティビティのストリームを返します。activity:read スコープが必要です。Only Me アクティビティには activity:read_all スコープが必要です。

パラメータ:

  * id::Int64 (必須)
  * keys::Vector{String} (必須)
  * key*by*type::Bool (必須)

返り値: StreamSet, OpenAPI.Clients.ApiResponse
