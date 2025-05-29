```
MultimodalStudentT <: Distribution{Multivariate,Continuous}
```

マルチモーダルスチューデントt分布（これは、[Caldwell et al.](https://arxiv.org/abs/1808.08051)で定義されたマルチモーダルコーシーと同様に定義されています）。

2つのバイモーダルピークがそれぞれ独自の次元に存在することを仮定します。

コンストラクタ:

  * `MultimodalStudentT(; μ::Real=1, σ::Float64=0.2, ν::Integer=1, n::Integer=4)`

引数:

  * `μ::Real`: 2つのバイモーダルピークに使用される位置パラメータ。
  * `σ::Float64`: すべてのコンポーネントで共有されるスケールパラメータ。
  * `ν::Int`: 自由度。
  * `n::Int`: 次元の数。

フィールド:

  * `bimodals::Distributions.MixtureModel`
  * `σ::Float64`
  * `n::Int64`
  * `dist::Distributions.Product`

!!! note
    `MultimodalStudentT`のすべてのフィールドは内部と見なされ、非推奨なしに変更される可能性があります。

