```
hermite_polynom(n::Integer [; msg=true])
```

The coefficients of [`hermiteH`](@ref) for degree `n`, 

$$
    v(n)=[c_0, c_1, \cdots\ c_n],
$$

where

$$
    c_k(n) = (-1)^{m}\frac{n!}{k!}\frac{2^{k}}{m!}
$$

with  $m = (n-k)/2$ and $k=0,1,⋯,n$.

  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Example:

```
julia> hermite_polynom(7)
(0, -1680, 0, 3360, 0, -1344, 0, 128)
```
