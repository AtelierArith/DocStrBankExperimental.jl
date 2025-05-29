```
generalized_laguerre_polynom(n::Int [, α=0 [; msg=true]])
```

The coefficients of [`generalized_laguerreL`](@ref) for degree `n` and parameter `α`, 

$$
    v(n, α)=[c_0, c_1, \cdots\ c_n],
$$

where

$$
    c_k(n, α) = \frac{\Gamma(α+n+1)}{\Gamma(α+k+1)}
    \frac{(-1)^{k}}{(n-k)!}\frac{1}{k!}
$$

with $k=0,1,⋯,n$. 

  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Example:

```
julia> o =  generalized_laguerre_polynom(6,3); println(o)
Rational{Int64}[84//1, -126//1, 63//1, -14//1, 3//2, -3//40, 1//720]

julia> o =  generalized_laguerre_polynom(6,3.0); println(o)
[84.0, -126.0, 63.0, -14.0, 1.5, -0.075, 0.001388888888888889]
```
