```
toDataFrame(idxtable::NDSparse)
```

単一値列のNDSParseテーブルを`DataFrame`に変換します。

# 引数

  * `idxtable`: 変換するNDSParseテーブル

# 例

```julia
julia> content = [["banana","banana","apple","apple","orange"],["us",missing,"us","eu","us"],[1.1,2.2,3.3,missing,5.5]]
julia> dimNames = ["item","region"]
julia> t = NDSparse(content...,names=Symbol.(dimNames))
julia> df = toDataFrame(t)
```
