```
NWState(nw_or_nw_wrapper, uflat, [pflat], [t])
```

フラット状態およびパラメータ配列のインデックス可能なラッパー。ネットワークまたはネットワークのラッパーが必要です。例：`ODEProblem`。

```
s = NWState(nw)
s.v[idx, :sym] # 頂点 idx の状態 :sym を取得
s.e[idx, :sym] # 辺 idx の状態 :sym を取得
s.p.v[idx, :sym] # 頂点 idx のパラメータ :sym を取得
s.p.e[idx, :sym] # 辺 idx のパラメータ :sym を取得
s[s::Union{VIndex, EIndex, EPIndex, VPIndex}] # 特定のインデックスのパラメータを取得
```

[`uflat`](@ref) および [`pflat`](@ref) を使用してフラット配列表現を取得します。フラット表現における状態の順序は [`variable_symbols`](@ref) によって与えられた順序に対応し、パラメータの順序は [`parameter_symbols`](@ref) に対応します。
