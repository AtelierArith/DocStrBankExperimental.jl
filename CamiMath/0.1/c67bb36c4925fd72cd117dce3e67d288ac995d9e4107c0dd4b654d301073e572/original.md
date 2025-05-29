```
polynom_product(polynom1, polynom2)
```

The coefficients of the product of two polynomials, a = `polynom1` and  b = `polynom2` of degree $m$ and $n$, which represents a polynomial  in a vector space of dimension $d=m+n+1$,

$$
    P(x)=a_0b_0 + (a_0b_1 + b_0a_1)x + ⋯ + a_n b_m x^{n+m}.
$$

#### Examples:

```
julia> polynom_product((1, 1), (1, -1, 2))
4-element Vector{Int64}:
 1
 0
 1
 2

julia> polynom_product((1, 1), (1, -1.0, 2))
4-element Vector{Real}:
 1
 0.0
 1.0
 2  
```
