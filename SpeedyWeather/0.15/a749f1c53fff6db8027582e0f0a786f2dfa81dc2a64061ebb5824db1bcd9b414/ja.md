以前のSpeedyWeather.jlシミュレーションを再起動するには、再起動ファイルrestart.jld2を使用します。これは水平方向での補間は行いますが、垂直方向では行いません。restart.jld2は以下によって特定されます。

  * `path::String`: 再起動ファイルのパス
  * `id::Union{Int64, String}`: `run_????/restart.jld2`内の再起動ファイルの`run_id`
