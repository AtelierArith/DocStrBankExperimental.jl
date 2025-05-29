```
polynom_product_expansion(polynom1, polynom2, p::Int)
```

The coefficients of the product of two polynomials, a = `polynom1`  (of degree $n$) and b = `polynom2` (of degree $m$), truncated at the  order `p`, which represents a polynomial in a vector space of  dimension $d=p+1$

#### Examples:

```
julia> a = (1,-1,1);

julia> b = (1,1,-1,1,1,1);

julia> o = polynom_product(a, b); println(o)
[1, 0, -1, 3, -1, 1, 0, 1]
 
julia> o = polynom_product_expansion(a, b, 4); println(o)
[1, 0, -1, 3, -1] 
```
