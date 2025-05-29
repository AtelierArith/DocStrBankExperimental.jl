```
max_distortion(D::PwMap; tol=1e-3)
```

PwMapの歪みの厳密な上限を計算します

# 例

```jldoctest
julia> using RigorousInvariantMeasures;

julia> D0 = mod1_dynamic(x->2*x+0.5*x*(1-x), full_branch = true)
2つのブランチを持つ分割定義動的

julia> max_distortion(D0)
[0.444268, 0.444445]
```
