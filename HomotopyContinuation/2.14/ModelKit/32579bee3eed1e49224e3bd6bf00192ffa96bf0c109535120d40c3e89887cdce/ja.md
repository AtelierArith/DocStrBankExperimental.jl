```
monomials(variables::AbstractVector, d::Integer; affine = true)
```

与えられた `variables` の指定された次数のすべての単項式を作成します。

```julia-repl
julia> @var x y
(x, y)

julia> monomials([x,y], 2; affine = false)
3-element Array{Operation,1}:
 x ^ 2
 x * y
 y ^ 2
```
