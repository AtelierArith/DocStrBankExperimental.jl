```
si_unit(u::Union{String, Symbol})
```

単一の単位のための乗法的SI単位変換係数を取得します。返される値は、`x*si_unit(:name)`が、指定された名前の単位のSI表現に`x`を変換するように与えられます。

# 例

```jldoctest
julia> si_unit(:day) # 秒として表された日
86400.0
```
