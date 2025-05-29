```
get_variables(e, varlist = nothing; sort::Bool = false)
```

Return a vector of variables appearing in `e`, optionally restricting to variables in `varlist`.

Note that the returned variables are not wrapped in the `Num` type.

# Examples

```jldoctest
julia> @variables t x y z(t);

julia> Symbolics.get_variables(x + y + sin(z); sort = true)
3-element Vector{SymbolicUtils.BasicSymbolic}:
 x
 y
 z(t)

julia> Symbolics.get_variables(x - y; sort = true)
2-element Vector{SymbolicUtils.BasicSymbolic}:
 x
 y
```
