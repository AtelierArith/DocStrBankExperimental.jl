```
fit(Hurdle,M,X,y; Xpos=Xpos, <keyword arguments>)
```

カウントベクトルyに対してHurdle (Mullahy, 1986)をXにフィットさせ、正のカウントをモデル化するために別の共変量行列Xposを使用する可能性があります。

# GLMの例:

```julia
  m = fit(Hurdle,GeneralizedLinearModel,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos)
```

# Lasso正則化の例:

```julia
  m = fit(Hurdle,GammaLassoPath,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos, select=MinAICc())
```

# 引数

  * `M::RegressionModel`
  * `counts` n-by-dのカウント行列（通常はスパース）
  * `dzero::UnivariateDistribution = Binomial()` ゼロモデルの分布
  * `dpos::UnivariateDistribution = PositivePoisson()` 正のモデルの分布
  * `lzero::Link=canonicallink(dzero)` ゼロモデルのリンク関数
  * `lpos::Link=canonicallink(dpos)` 正のモデルのリンク関数

# キーワード

  * `Xpos::Union{AbstractMatrix{T},Nothing} = nothing` 正のモデルのための共変量行列、または両方の部分にXを使用するためのnothing
  * `dofit::Bool = true` モデルをフィットさせるか、単にそのシェルを構築するか
  * `wts::V = ones(y)` 観測重み
  * `offsetzero::AbstractVector = similar(y, 0)` ゼロモデルのオフセット
  * `offsetpos::AbstractVector = similar(y, 0)` 正のモデルのオフセット
  * `offset::AbstractVector = similar(y, 0)` 両方のモデル部分のオフセット
  * `verbose::Bool=true`
  * `showwarnings::Bool=false`
  * `fitargs...` fit(M,...)に渡される追加のキーワード引数

```
