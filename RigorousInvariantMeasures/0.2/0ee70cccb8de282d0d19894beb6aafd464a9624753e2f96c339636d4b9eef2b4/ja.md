```
mod1_dynamic(f::Function, ε = 0.0; full_branch = false)
```

トーラス [0,1] 上の動的 Mod 1 のユーティリティコンストラクタ。ここでは f が単調で微分可能であると仮定します（これは私たちの目的には制限的ではありません）。

# 例

```jldoctest
julia> using RigorousInvariantMeasures;

julia> D0 = mod1_dynamic(x->2*x+0.5*x*(1-x), full_branch = true)
2 つのブランチを持つ分割定義された動的
```
