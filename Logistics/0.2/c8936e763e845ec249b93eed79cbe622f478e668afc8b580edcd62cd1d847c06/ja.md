```
Logistic{T<:AbstractFloat} <: Real

Logistic(t::Real)
Logistic{T}(t::Real) where {T<:AbstractFloat}
```

$$
[0,1]
$$

の範囲の実数（例えば確率）をそのロジット値で表す型です。

!!! warning
    数値型を変換するために`Logistic`を使用しないでください！例えば、`Logistic(0.39)`は値として$0.39$ではなく、$\operatorname{logistic}(0.39) \approx 0.60$に等しいです。数値を同等の`Logistic`インスタンスに変換するには、[`logisticate`](@ref)または`convert(Logistic, x)`を使用してください。

