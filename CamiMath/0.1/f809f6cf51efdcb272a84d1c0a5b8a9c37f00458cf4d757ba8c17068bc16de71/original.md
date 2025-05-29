```
polynomial(polynom, x::T [; deriv=0]) where T<:Real
```

Polynomial of degree $d$,

$$
    P(x)=c_0 + c_1 x + ⋯ + c_d x^d,
$$

where the coefficients `polynom` = $(c_0,⋯\ c_d)$ define the vector  representation of the polynomial in a vector space of dimension $d+1$.

#### Examples:

```
julia> polynom = (1, 1, 1, 1, 1);
           
julia> P(x) = polynomial(polynom,x);

julia> P(1)
5

julia> polynomial(polynom, 1; deriv=1)     # P′(1)
10

julia> polynomial(polynom, 2; deriv=2)     # P″(1)
20

julia> polynomial(polynom, 1; deriv=-1)   # primitive (zero integration constant)
137 // 60
```
