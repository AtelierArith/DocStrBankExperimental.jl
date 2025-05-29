```
quantile(model::AbstractExtremeValueModel, θ::Vector{<:Real}, p::Real)
```

モデル `AbstractExtremeValueModel` でレベル `p` の分位数を計算します。`θ` で指定されたパラメータに基づいています。

モデルが非定常の場合、*効果的分位数* が返されます。すなわち、各共変量の値に対して1つずつです。
