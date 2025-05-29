```
struct EqualityConstraint
```

線形等式制約を表します。

# フィールド

  * `ts::AbstractArray{Int}`: 制約が適用される時間ステップ
  * `js::AbstractArray{Int}`: 制約が適用される軌道の成分
  * `vals::Vector{R}`: 制約の値
  * `vardim::Int`: 軌道の単一時間ステップの次元
  * `label::String`: 制約のラベル
