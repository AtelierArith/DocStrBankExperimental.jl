```
inspace(vn::Union{VarName, Symbol}, space::Tuple)
```

Check whether `vn`'s variable symbol is in `space`.  The empty tuple counts as the "universal space" containing all variables. Subsumption (see [`subsumes`](@ref)) is respected.

## Examples

```jldoctest
julia> inspace(@varname(x[1][2:3]), ())
true

julia> inspace(@varname(x[1][2:3]), (:x,))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x),))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x[1:10]), :y))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x[:][2:4]), :y))
true

julia> inspace(@varname(x[1][2:3]), (@varname(x[1:10]),))
true
```
