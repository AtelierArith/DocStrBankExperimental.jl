```
get_variables(O) -> Vector{BasicSymbolic}
```

Returns the variables in the expression. Note that the returned variables are not wrapped in the `Num` type.

# Examples

```julia
julia> @variables t x y z(t)
4-element Vector{Num}:
    t
    x
    y
 z(t)

julia> ex = x + y + sin(z)
(x + y) + sin(z(t))

julia> Symbolics.get_variables(ex)
3-element Vector{Any}:
 x
 y
 z(t)
```
