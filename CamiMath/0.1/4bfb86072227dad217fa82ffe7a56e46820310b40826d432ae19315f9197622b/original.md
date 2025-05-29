```
faulhaber_polynom(p::Integer [; msg=true])
```

Vector representation of the coefficients of the [`faulhaber_polynomial`](@ref)  of degree `p`, 

$$
   c=[c_0,⋯\ c_p],
$$

where $c_0=0,\ \ c_j=\frac{1}{p}{\binom{p}{p-j}}B_{p-j}$, with $j∈\{ 1,⋯\ p\}$. The $B_{p-j}$ are [`bernoulliB`](@ref) in the  *even index convention* (but with  $B_1=+\frac{1}{2}$ rather than $-\frac{1}{2}$).

  * `msg` : integer-overflow protection (IOP) - warning on activation

(for `p > 36`)

#### Example:

```
faulhaber_polynom(6)
7-element Vector{Rational{Int64}}:
  0//1
  0//1
 -1//12
  0//1
  5//12
  1//2
  1//6
```
