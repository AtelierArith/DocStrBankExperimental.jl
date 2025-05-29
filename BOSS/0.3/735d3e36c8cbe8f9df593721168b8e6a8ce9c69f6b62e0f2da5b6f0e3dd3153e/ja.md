```
model_posterior_slice(::BossProblem, slice::Int) -> post
```

与えられた出力 `slice` の事後予測分布を2つのメソッドで返します：

  * `post(x::AbstractVector{<:Real}) -> μ::Real, σ::Real`
  * `post(X::AbstractMatrix{<:Real}) -> μ::AbstractVector{<:Real}, Σ::AbstractMatrix{<:Real}`

最初のメソッドは、`Domain` からの長さ `x_dim(::BossProblem)` の単一の点 `x` を取り、対応する出力数 `y` の予測平均と偏差を返します：

  * `μ, σ = post(x)` => `y ∼ Normal(μ, σ)`

2番目のメソッドは、サイズ `(x_dim, N)` の列方向の行列 `X` から複数の点を取り、対応する出力ベクトル `y` の結合予測平均と共分散行列を返します：

  * `μ, Σ = post(X)` => `y ∼ MvNormal(μ, Σ)`

特定の出力次元の予測にのみ関心がある場合、`model_posterior_slice` を使用する方が `model_posterior` よりも効率的である可能性があります（使用される `SurrogateModel` に依存します）。

`model_posterior_slice` は `sliceable(model) == false` の場合でも使用できますが、その場合は追加の効率を提供しません。

参照： [`model_posterior`](@ref)
