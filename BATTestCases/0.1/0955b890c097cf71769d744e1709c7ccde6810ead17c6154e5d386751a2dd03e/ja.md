```
struct GaussianShell <: Distribution{Multivariate,Continuous}
```

*実験的な機能であり、安定した公開APIの一部ではありません。*

ガウシアンシェル（定義については[Caldwell et al.](https://arxiv.org/abs/1808.08051)を参照）。

コンストラクタ:

  * `GaussianShell(; r::Real=5, w::Real=2, n::Integer=2)`

フィールド:

  * `r::Real`: ガウシアンシェル分布の半径。
  * `w::Real`: ガウシアンシェル分布の分散
  * `n::Int64`: 次元数
  * `c::AbstractVector{<:Real}`
  * `lognorm::AbstractFloat`

!!! note
    フィールド `c` と `lognorm` は内部的なものであり、非推奨なしに変更される可能性があります。

