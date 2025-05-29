アスリートの活動のリスト

特定の識別子に対するアスリートの活動を返します。activity:readが必要です。activity:read_allのトークンで要求されない限り、Only Meの活動はフィルタリングされます。

パラメータ:

  * before::Int64
  * after::Int64
  * page::Int64
  * per_page::Int64

返り値: Vector{SummaryActivity}, OpenAPI.Clients.ApiResponse
