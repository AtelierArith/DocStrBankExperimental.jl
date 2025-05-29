```
NWParameter(nw_or_nw_wraper, pflat)
```

フラットパラメータ配列 `pflat` のインデックス可能なラッパー。ネットワークまたはネットワークのラッパー、例えば `ODEProblem` が必要です。

```
p = NWParameter(nw)
p.v[idx, :sym] # 頂点 idx のパラメータ :sym を取得
p.e[idx, :sym] # 辺 idx のパラメータ :sym を取得
p[s::Union{VPIndex, EPIndex}] # 特定のインデックスのパラメータを取得
```

フラット配列表現を [`pflat`](@ref) を使用して取得します。フラット表現におけるパラメータの順序は、[`parameter_symbols`](@ref) によって与えられた順序に対応しています。
