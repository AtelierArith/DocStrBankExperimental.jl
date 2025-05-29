```
initiate_output_datasets(output_files::Vector{String}, x_len::Int64, y_len::Int64,
                         output_bands::Vector, reference_dataset::ArchGDAL.IDataset)
```

指定された寸法とバンド情報を使用して、参照データセットを用いて投影とジオトランスフォーメーションを行い、ENVI形式の複数の出力ラスターデータセットを初期化します。

# 引数

  * `output_files::Vector{String}`: 出力データセットのファイルパス。各エントリは

別々の出力ラスタに対応します。

  * `x_len::Int64`: 出力データセットの幅。
  * `y_len::Int64`: 出力データセットの高さ。
  * `output_bands::Vector`: 各出力データセットのバンド数。このベクターの長さは

`output_files`の長さと一致する必要があります。

  * `reference_dataset::ArchGDAL.IDataset`: 投影とジオトランスフォーメーション情報がコピーされる参照データセットオブジェクト。

# 注意事項

  * 出力データセットのすべてのバンドは、ノーデータ値`-9999`で初期化されます。
