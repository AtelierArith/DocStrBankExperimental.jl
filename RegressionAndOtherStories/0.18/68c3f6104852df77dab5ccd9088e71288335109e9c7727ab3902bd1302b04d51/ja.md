# スケール!

1つ以上の列のスケーリングされた値でDataFrameを拡張します

### メソッド

```julia
scale!(df, var, ext) 
```

### 必要な引数

```julia
* `df::DataFrame`                      : DataFrame
* `var::Union{Symbol, Vector{Symbol}}` : スケーリングする変数
* `ext::String="_s"`                   : スケーリングされた変数のサフィックス
```

### 戻り値

```julia
* `result::DataFrame`                  : 拡張されたDataFrame
```

### 例

```julia
scale!(df, :var1)

または

scale!(mydf, [:var1, var2])
```
