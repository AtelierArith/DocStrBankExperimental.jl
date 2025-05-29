```
getSafe(idxtable,indices,missingValue=missing)
```

指定されたキーが存在しない場合、NDSParseテーブルに格納されている値を返すか、missingValueを返します。

# 引数

  * `idxtable`: ルックアップするNDSParseテーブル
  * `indices`: 使用するインデックスのタプル（`:`がサポートされています）
  * `missingValue`: 指定されたキーが見つからない場合に返す値

# 例

```julia
julia> volBlackForest2014  = getSafe(forestVolumes,("BlackForest",2014),0.0)
```
