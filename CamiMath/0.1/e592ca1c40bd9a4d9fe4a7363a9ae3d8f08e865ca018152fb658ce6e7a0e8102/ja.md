```
generalized_laguerreL(n::Integer, α, x::T [; deriv=0 [, msg=true]]) where T<:Real
```

パラメータ `α` に対する次数 `n` の一般化ラゲール多項式、

$$
    L_{n}^{α}(x)
    = \frac{1}{n!}e^{x}x^{-α}\frac{d^{n}}{dx^{n}}(e^{-x}x^{n+α})
    = \sum_{k=0}^{n}(-1)^{k}\binom{n+α}{n-k}\frac{x^{k}}{k!}
    = \sum_{k=0}^{n}c_k(n,α)x^{k}
$$

ここで、$c_k(n,α)$ は [`generalized_laguerre_polynom`](@ref) の一般化ラゲール係数です。

#### 例:

```
julia> polynom = generalized_laguerre_polynom(5, 3); println(polynom)
Rational{Int64}[56//1, -70//1, 28//1, -14//3, 1//3, -1//120]

julia> polynomial(polynom, 10.0)
-10.666666666667311

julia> generalized_laguerreL(5, 3, 10.0)
-10.666666666667311
```
