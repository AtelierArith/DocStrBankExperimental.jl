```
monomials(variables::AbstractVector, d::Integer; affine = true)
```

Create all monomials of a given degree in the given `variables`.

```julia-repl
julia> @var x y
(x, y)

julia> monomials([x,y], 2; affine = false)
3-element Array{Operation,1}:
 x ^ 2
 x * y
 y ^ 2
```
