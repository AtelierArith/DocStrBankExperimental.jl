```
const Operator = Union{Connective,Truth}
```

Union type for logical constants of any ariety (zero for `Truth` values, non-zero for `Connective`s).

See also [`Connective`](@ref), [`Truth`](@ref).
