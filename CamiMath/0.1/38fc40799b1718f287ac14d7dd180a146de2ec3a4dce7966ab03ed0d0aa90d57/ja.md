```
generalized_laguerre_polynom(n::Int [, α=0 [; msg=true]])
```

[`generalized_laguerreL`](@ref) の係数は、次数 `n` とパラメータ `α` に対して、

$$
    v(n, α)=[c_0, c_1, \cdots\ c_n],
$$

ここで

$$
    c_k(n, α) = \frac{\Gamma(α+n+1)}{\Gamma(α+k+1)}
    \frac{(-1)^{k}}{(n-k)!}\frac{1}{k!}
$$

であり、$k=0,1,⋯,n$ です。

  * `msg` : 整数オーバーフロー保護 (IOP) - 有効化時に警告

#### 例:

```
julia> o =  generalized_laguerre_polynom(6,3); println(o)
Rational{Int64}[84//1, -126//1, 63//1, -14//1, 3//2, -3//40, 1//720]

julia> o =  generalized_laguerre_polynom(6,3.0); println(o)
[84.0, -126.0, 63.0, -14.0, 1.5, -0.075, 0.001388888888888889]
```
