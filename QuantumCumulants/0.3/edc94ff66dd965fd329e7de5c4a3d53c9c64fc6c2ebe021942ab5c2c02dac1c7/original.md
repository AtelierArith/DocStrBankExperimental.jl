```
cumulant(x,n=get_order(x);simplify=true,kwargs...)
```

Compute the `n`th cumulant of `x` (either an operator or an average). The output is simplified when `simplify=true`. Further keyword arguments are passed on to simplification.

# Examples

```
julia> cumulant(a)
⟨a⟩

julia> cumulant(a*b)
(⟨a*b⟩+(-1*⟨a⟩*⟨b⟩))

julia> cumulant(a*b,1)
⟨a*b⟩

julia> cumulant(a*b,3)
0
```
