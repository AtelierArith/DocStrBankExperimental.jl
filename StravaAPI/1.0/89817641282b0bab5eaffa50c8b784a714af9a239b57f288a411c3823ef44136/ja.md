セグメントストリームを取得

指定されたセグメントのストリームを返します。プライベートセグメントには read_all スコープが必要です。

パラメータ:

  * id::Int64 (必須)
  * keys::Vector{String} (必須)
  * key*by*type::Bool (必須)

返却: StreamSet, OpenAPI.Clients.ApiResponse
