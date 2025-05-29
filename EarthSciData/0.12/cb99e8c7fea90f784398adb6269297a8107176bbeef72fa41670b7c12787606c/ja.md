`EarthSciMLBase.Operator`を作成して、シミュレーション出力をNetCDFファイルに書き込みます。

  * `filepath::String`: 書き込むNetCDFファイルのパス
  * `file::Any`: netcdfデータセット
  * `vars::Any`: 状態変数に対応するnetcdf変数
  * `tvar::Any`: 時間のためのnetcdf変数
  * `h::Int64`: 書き込みのための現在の時間インデックス
  * `time_interval::AbstractFloat`: ディスクに書き込むシミュレーション時間間隔（秒単位）
  * `extra_vars::AbstractVector`: ディスクに書き込む追加の観測変数
  * `extra_var_fs::AbstractVector`: 追加の変数を取得するための関数
  * `grid::Any`: 空間グリッドの仕様
  * `dtype::Any`: 出力のデータ型
