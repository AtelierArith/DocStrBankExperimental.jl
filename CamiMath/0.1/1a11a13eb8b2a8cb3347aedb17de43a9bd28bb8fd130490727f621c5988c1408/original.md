```
faulhaber_polynomial(n::Integer, p::Int [; msg=true])
```

Faulhaber polynomial of degree `p` 

$$
    F(n,p)=\sum_{j=0}^{p}c_{j}n^{j},
$$

where `n` is a positive integer and the coefficients are contained in the  vector $c=[c_0,⋯\ c_p]$ given by [`faulhaber_polynom`](@ref).

  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Examples:

```
julia> faulhaber_polynomial(3, 6)
276

julia> faulhaber_polynomial(5, 30)
IOP capture: faulhaber_polynomial(5, 30) autoconverted to Rational{BigInt}
186552813930161650665
```
