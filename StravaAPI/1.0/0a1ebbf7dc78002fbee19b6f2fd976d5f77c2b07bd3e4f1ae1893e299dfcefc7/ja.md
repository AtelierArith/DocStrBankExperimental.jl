アスリートルートのリスト

認証されたアスリートによって作成されたルートのリストを返します。プライベートルートは、read_allスコープを持つトークンによって要求されない限り、フィルタリングされます。

パラメータ:

  * page::Int64
  * per_page::Int64

返却: Vector{Route}, OpenAPI.Clients.ApiResponse
