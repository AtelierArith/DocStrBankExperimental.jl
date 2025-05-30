```
OptimalBranchingResult{INT <: Integer}
```

最適分岐ルールの結果タイプ。

### フィールド

  * `optimal_rule::DNF{INT}`: 最適分岐ルール。
  * `branching_vector::Vector{T<:Real}`: 各サブ問題におけるサイズ削減を記録する分岐ベクトル。
  * `γ::Float64`: 最適な γ 値（分岐ルールの複雑さ）。
