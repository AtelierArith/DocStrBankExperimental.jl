netCDFファイルの出力ライターで、(再)グリッド化された変数を扱います。非矩形グリッドを補間します。フィールドは次の通りです。

  * `active::Bool`
  * `path::String`: [OPTION] 出力フォルダーへのパス、run_????がその中に作成されます
  * `id::String`: [OPTION] 実行識別番号/文字列
  * `run_path::String`
  * `filename::String`: [OPTION] 出力netcdfファイルの名前
  * `write_restart::Bool`: [OPTION] output==trueの場合、再起動ファイルも書き込みますか？
  * `pkg_version::VersionNumber`
  * `startdate::Dates.DateTime`
  * `output_dt::Dates.Second`: [OPTION] 出力頻度、時間ステップ
  * `variables::Dict{Symbol, SpeedyWeather.AbstractOutputVariable}`: [OPTION] 出力する変数の辞書、例: u, v, vor, div, pres, temp, humid
  * `output_every_n_steps::Int64`
  * `timestep_counter::Int64`
  * `output_counter::Int64`
  * `netcdf_file::Union{Nothing, NCDatasets.NCDataset}`
  * `interpolator::Any`
  * `grid2D::Any`
  * `grid3D::Any`
  * `grid3Dland::Any`
