```
predict(m,X; Xpos=Xpos, <キーワード引数>)
```

新しい X（および潜在的に Xpos）を使用して、適合した TwoPartModel を予測します。

# GLM の例:

```julia
  m = fit(Hurdle,GeneralizedLinearModel,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos)
```

# Lasso 正則化の例:

```julia
  m = fit(Hurdle,GammaLassoPath,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos, select=MinAICc())
```

# 引数

  * `m::Hurdle` 適合した Hurdle モデル
  * `X` m を適合させるために使用されたのと同じ次元の n-by-p の共変量行列。

# キーワード

  * `Xpos::Union{AbstractMatrix{T},Nothing} = nothing` 正のモデル用の共変量行列、または両方の部分に X を使用するための何もない
  * `kwargs...` 2 つのモデル部分のそれぞれに対して predict() に渡される追加のキーワード引数。
