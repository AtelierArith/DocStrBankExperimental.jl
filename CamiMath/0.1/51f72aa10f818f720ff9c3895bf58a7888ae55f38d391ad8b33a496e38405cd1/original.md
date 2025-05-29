```
laguerre_polynom(n::Integer [; msg=true])
```

The coefficients of [`laguerreL`](@ref) for degree `n`, 

$$
    v(n)=[c_0, c_1, \cdots\ c_n],
$$

where

$$
    c_k(n) = \frac{\Gamma(n+1)}{\Gamma(k+1)}\frac{(-1)^{k}}{(n-k)!}\frac{1}{k!}
$$

with $k=0,1,⋯,n$.

  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Example:

```
julia> laguerre_polynom(7)
(1//1, -7//1, 21//2, -35//6, 35//24, -7//40, 7//720, -1//5040)
```
