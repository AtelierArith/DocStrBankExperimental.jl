```
antidifferentiate(p::AbstractPolynomialLike, v::AbstractVariable, deg::Union{Int, Val}=1)
```

Antidifferentiate `deg` times the polynomial `p` by the variable `v`. The free constant involved by the antidifferentiation is set to 0.

```
antidifferentiate(p::AbstractPolynomialLike, vs, deg::Union{Int, Val}=1)
```

Antidifferentiate `deg` times the polynomial `p` by the variables of the vector or tuple of variable `vs` and return an array of dimension `deg`. It is recommended to pass `deg` as a `Val` instance when the degree is known at compile time, e.g. `antidifferentiate(p, v, Val{2}())` instead of `antidifferentiate(p, x, 2)`, as this will help the compiler infer the return type.

### Examples

```julia
p = 3x^2*y + x + 2y + 1
antidifferentiate(p, x) # should return 3x^3* + 1/2*x + 2xy + x
antidifferentiate(p, x, Val{1}()) # equivalent to the above
antidifferentiate(p, (x, y)) # should return [3x^3* + 1/2*x + 2xy + x, 3/2x^2*y^2 + xy + y^2 + y]
```
