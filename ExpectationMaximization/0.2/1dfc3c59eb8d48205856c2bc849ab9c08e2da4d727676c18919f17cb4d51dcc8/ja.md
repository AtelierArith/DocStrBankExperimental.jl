```
fit_mle!(α::AbstractVector, dists::AbstractVector{F} where {F<:Distribution}, y::AbstractVecOrMat, method::ClassicEM; display=:none, maxiter=1000, atol=1e-3, rtol=nothing, robust=false)
```

EMアルゴリズムを使用して、混合分布を構成する分布 `dists` と重み `α` を更新します。

  * `robust = true` は、(対数)尤度が `-∞` または `∞` にオーバーフローするのを防ぎます。
  * `atol` はアルゴリズムの収束を決定する基準です。2つの反復 `i` と `i+1` の間の対数尤度の差が `atol` より小さい場合、すなわち `|ℓ⁽ⁱ⁺¹⁾ - ℓ⁽ⁱ⁾|<atol` の場合、アルゴリズムは停止します。
  * `rtol` は収束のための相対許容誤差であり、`|ℓ⁽ⁱ⁺¹⁾ - ℓ⁽ⁱ⁾|<rtol*(|ℓ⁽ⁱ⁺¹⁾| + |ℓ⁽ⁱ⁾|)/2` （`rtol` が `nothing` であるかどうかはチェックしません）
  * `display` の値は `:none`、`:iter`、`:final` のいずれかで、各反復での対数尤度の進行状況を表示するか、最終的なものだけを表示します `:final`
