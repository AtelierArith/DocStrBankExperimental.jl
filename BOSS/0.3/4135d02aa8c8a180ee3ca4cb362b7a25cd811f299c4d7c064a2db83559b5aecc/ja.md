```
model_posterior(::BossProblem) -> post
```

サロゲートモデルの事後予測分布を2つのメソッドで返します：

  * `post(x::AbstractVector{<:Real}) -> μs::AbstractVector{<:Real}, σs::AsbtractVector{<:Real}`
  * `post(X::AbstractMatrix{<:Real}) -> μs::AbstractMatrix{<:Real}, Σs::AbstractArray{<:Real, 3}`

最初のメソッドは、`Domain`からの長さ`x_dim(::BossProblem)`の単一点`x`を受け取り、対応する出力ベクトル`y`の予測平均と偏差を返します。`y`の長さは`y_dim(::BossProblem)`であり、次のようになります：

  * `μs, σs = post(x)` => `y ∼ product_distribution(Normal.(μs, σs))`
  * `μs, σs = post(x)` => `y[i] ∼ Normal(μs[i], σs[i])`

2番目のメソッドは、`Domain`からの複数の点を列方向の行列`X`として受け取り、そのサイズは`(x_dim, N)`であり、対応する出力行列`Y`の結合予測平均と共分散行列を返します。`Y`のサイズは`(y_dim, N)`であり、次のようになります：

  * `μs, Σs = post(X)` => `transpose(Y) ∼ product_distribution(MvNormal.(eachcol(μs), eachslice(Σs; dims=3)))`
  * `μs, Σs = post(X)` => `Y[i,:] ∼ MvNormal(μs[:,i], Σs[:,:,i])`

参照： [`model_posterior_slice`](@ref)
