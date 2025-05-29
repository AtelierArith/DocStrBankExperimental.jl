```
@equations model begin
    :eqnkey => lhs = rhs
    lhs = rhs
    ...
end
```

Replace equations with the given keys with the equation provided. Equations provided without a key or with a non-existing key will be added to the model. The keys must be provided with their full symbol reference, including the `:`.

To find the key for an equation, see [`summarize`](@ref). For equation details, see [`Equation`](@ref).

Changes like this should be followed by a call to [`@reinitialize`](@ref) on the model.
