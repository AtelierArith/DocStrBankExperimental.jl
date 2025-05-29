```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LogisticRegression, Link::Cauchit; kwargs...)
```

Cauchitリンクを使用して入力データに対してロジスティック回帰モデルをフィットします。内部では[GLM](https://github.com/JuliaStats/GLM.jl)パッケージの[glm](https://juliastats.org/GLM.jl/stable/api/#GLM.glm)メソッドを使用します。`FrequentistRegression{:LogisticRegression}`型のオブジェクトを返します。glmと同じキーワード引数をサポートしています。
