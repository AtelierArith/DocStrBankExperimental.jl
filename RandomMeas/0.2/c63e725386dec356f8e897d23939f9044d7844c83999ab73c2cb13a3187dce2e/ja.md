```
apply_map(map::MPO,state::MPO,s::Vector{Index{Int64}},ξ::Vector{Index{Int64}})
```

インデックスの状態 (ξ,ξ') に対してマップ map((s,s')→(ξ,ξ')) を適用します。
