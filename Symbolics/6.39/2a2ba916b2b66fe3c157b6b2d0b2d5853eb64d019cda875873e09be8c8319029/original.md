```
substitute(expr, s; fold=true)
```

Performs the substitution on `expr` according to rule(s) `s`. If `fold=false`, expressions which can be evaluated won't be evaluated.

# Examples

```jldoctest
julia> @variables t x y z(t)
4-element Vector{Num}:
    t
    x
    y
 z(t)
julia> ex = x + y + sin(z)
(x + y) + sin(z(t))
julia> substitute(ex, Dict([x => z, sin(z) => z^2]))
(z(t) + y) + (z(t) ^ 2)
julia> substitute(sqrt(2x), Dict([x => 1]); fold=false)
sqrt(2)
```
