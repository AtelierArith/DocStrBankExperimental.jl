```
FFE
```

GAPのFFE（"有限体要素"）即時オブジェクトへのポインタをラップします。このタイプはJuliaInterface Cコードで定義されています。

# 例

```jldoctest
julia> x = GAP.Globals.Z(3)
GAP: Z(3)

julia> typeof(x)
FFE
```
