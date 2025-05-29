```
load_dataset(dataset::String) -> YAXArray
load_dataset(dataset::String) -> DataFrame
```

指定されたデータセットをロードし、ロードされたパッケージに応じてYAXArrayまたはDataFrameに変換します。

# 引数

  * `dataset::String`: ロードするデータセットの名前。現在は「sentinel」と「spectral」をサポートしています。

# 戻り値

  * YAXArraysが名前空間にロードされている場合、ロードされたデータセットを含む`YAXArray`オブジェクトを返し、次元は`:x`、`:y`、および`:bands`としてラベル付けされます。空間次元（`:x`および`:y`）はそれぞれ300のサイズを持つと仮定され、`:bands`次元には["B02", "B03", "B04", "B08"]バンドが含まれます。
  * DataFramesが名前空間にロードされている場合、データセットがロードされた`DataFrame`を返します。

# エラー

`dataset`引数が事前定義されたデータセット名のいずれかと一致しない場合、エラーをスローします。

# 例

```julia
# YAXArrayとしてデータセットをロード
yax_ds = SpectralIndices.load_dataset("sentinel")

# DataFrameとしてデータセットをロード
df_ds = SpectralIndices.load_dataset("spectral")
```

現在の実装では、JSONファイル（「sentinel」用の「S2_10m.json」と「spectral」用の「spectral.json」）が特定の形式に従うことを期待しています：各内部ベクトルがYAXArrayバージョンの300x300空間グリッド内のバンドデータを表すベクトルのベクトル、またはDataFrameバージョンに直接変換できる適切な構造。ファイルはすでにパッケージ内の`data`フォルダーに例として提供されています。 ```
