アクティビティを作成する

アスリートのための手動アクティビティを作成し、activity:write スコープが必要です。

パラメータ:

  * name::String (必須)
  * sport_type::String (必須)
  * start*date*local::ZonedDateTime (必須)
  * elapsed_time::Int64 (必須)
  * type::String
  * description::String
  * distance::Float32
  * trainer::Int64
  * commute::Int64

戻り値: DetailedActivity, OpenAPI.Clients.ApiResponse
