```
read_combined_h5(filename::AbstractString; show_warnings::Bool=true, error_on_missing_coordinates::Bool=true, pattern::Regex=r"", kw...)
```

スタックを使用してルート ("/") から HDF5 ファイルを反復的にトラバースします。

# 引数

  * `filename`: 結合された HDF5 ファイルへのパス
  * `error_on_missing_coordinates` (デフォルト `true`): ディスパッチ中の座標チェックを強制
  * `pattern` (デフォルト `r""`): 処理されるパスをフィルタリングするために使用される正規表現
  * `kw...`: `hdf2imas` に渡される追加のキーワード引数

# 戻り値

  * `Dict{String,Any}`: キー (文字列としてのパス) を持つ読み込まれたデータ
