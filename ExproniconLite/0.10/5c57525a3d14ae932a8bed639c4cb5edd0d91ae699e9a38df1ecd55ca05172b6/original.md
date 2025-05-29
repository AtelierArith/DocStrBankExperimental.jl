```
Substitute(condition) -> substitute(f(expr), expr)
```

Returns a function that substitutes `expr` with `f(expr)` if `condition(expr)` is true. Applied recursively to all sub-expressions.

# Example

```jldoctest
julia> sub = Substitute() do expr
           expr isa Symbol && expr in [:x] && return true
           return false
       end;

julia> sub(_->1, :(x + y))
:(1 + y)
```
