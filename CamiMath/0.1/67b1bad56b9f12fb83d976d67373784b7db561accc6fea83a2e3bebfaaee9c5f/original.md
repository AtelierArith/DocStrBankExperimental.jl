```
faulhaber_summation(n::Integer, p::Int [; msg=true])
```

Sum of the $p^{th}$ power of the first $n$ natural numbers

$$
    \sum_{k=1}^{n}k^{p}=H_{n,-p}=F(n,p+1).
$$

where $H_{n,-p}$ is a [`harmonicNumber`](@ref)  of power `-p` and $F(n,p)$  a [`faulhaber_polynomial`](@ref) of power `p`.

  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Examples:

```
julia> faulhaber_summation(3,5)
276

julia> faulhaber_summation(3,60)
IOP capture: faulhaber_polynom autoconverted to Rational{BigInt}
42391158276369125018901280178
```
