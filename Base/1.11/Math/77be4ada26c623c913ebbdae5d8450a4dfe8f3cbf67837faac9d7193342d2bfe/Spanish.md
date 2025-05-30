```
exp(x)
```

Calcula la exponencial de base natural de `x`, en otras palabras $ℯ^x$.

Véase también [`exp2`](@ref), [`exp10`](@ref) y [`cis`](@ref).

# Ejemplos

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```
