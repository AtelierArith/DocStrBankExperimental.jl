リストセグメント努力

認証されたアスリートの特定のセグメントに対するセグメント努力のセットを返します。サブスクリプションが必要です。

パラメータ:

  * segment_id::Int64 (必須)
  * start*date*local::ZonedDateTime
  * end*date*local::ZonedDateTime
  * per_page::Int64

返却: Vector{DetailedSegmentEffort}, OpenAPI.Clients.ApiResponse
