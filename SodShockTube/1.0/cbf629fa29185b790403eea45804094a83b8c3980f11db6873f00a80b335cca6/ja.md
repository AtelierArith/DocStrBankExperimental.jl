```
ShockTubeProblem
```

衝撃管問題のパラメータを含む

# フィールド

`geometry::Tuple{Float64, Float64, Float64}` (左端、右端、初期衝撃位置) の位置を含む

`left_state` 不連続性の左側の完全に指定された熱力学状態 (p, ρ, u の NamedTuple)

`right_state` 不連続性の右側の完全に指定された熱力学状態 (p, ρ, u の NamedTuple)

`t::Float64` 衝撃管問題が解かれる時刻

`γ::Float64` 衝撃管内のガスの比熱比
