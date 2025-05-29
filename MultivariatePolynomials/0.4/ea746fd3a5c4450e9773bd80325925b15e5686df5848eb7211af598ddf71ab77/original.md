```
differentiate(p::AbstractPolynomialLike, v::AbstractVariable, deg::Union{Int, Val}=1)
```

Differentiate `deg` times the polynomial `p` by the variable `v`.

```
differentiate(p::AbstractPolynomialLike, vs, deg::Union{Int, Val}=1)
```

Differentiate `deg` times the polynomial `p` by the variables of the vector or tuple of variable `vs` and return an array of dimension `deg`. It is recommended to pass `deg` as a `Val` instance when the degree is known at compile time, e.g. `differentiate(p, v, Val{2}())` instead of `differentiate(p, x, 2)`, as this will help the compiler infer the return type.

```
differentiate(p::AbstractArray{<:AbstractPolynomialLike, N}, vs, deg::Union{Int, Val}=1) where N
```

Differentiate the polynomials in `p` by the variables of the vector or tuple of variable `vs` and return an array of dimension `N+deg`. If `p` is an `AbstractVector` this returns the Jacobian of `p` where the i-th row containts the partial derivaties of `p[i]`.

### Examples

```julia
p = 3x^2*y + x + 2y + 1
differentiate(p, x) # should return 6xy + 1
differentiate(p, x, Val{1}()) # equivalent to the above
differentiate(p, (x, y)) # should return [6xy+1, 3x^2+1]
differentiate( [x^2+y, z^2+4x], [x, y, z]) # should return [2x 1 0; 4 0 2z]
```
