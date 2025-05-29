```
difference_of_convex_proximal_point!(M, grad_h, p; cost=nothing, kwargs...)
difference_of_convex_proximal_point!(M, mdcpo, p; cost=nothing, kwargs...)
difference_of_convex_proximal_point!(M, mdcpo, prox_g, p; cost=nothing, kwargs...)
```

凸の差分アルゴリズムを計算して最小化します

$$
    \operatorname*{arg\,min}_{p∈\mathcal M} g(p) - h(p)
$$

ここで、`g`の近接写像と`h`の勾配を提供する必要があります。

計算は`p`のインプレースで行われます。

キーワード引数を含むすべての詳細については、[`difference_of_convex_proximal_point`](@ref)を参照してください。
