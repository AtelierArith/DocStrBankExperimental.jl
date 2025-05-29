```
polynom_power(polynom, p)
```

The `polynom` of a polynomial of degree $d$ raised to the power `p`, which define a polynomial in a vector space of dimension $p d + 1$.

#### Examples:

```
julia> polynom = (1,1,1)    # coordinates of polynomial vector of degree d = 2
(1, 1, 1)

julia> polynom = (1,1,1);

julia> polynom_power(polynom, 3)
7-element Vector{Int64}:
 1
 3
 6
 7
 6
 3
 1
```
