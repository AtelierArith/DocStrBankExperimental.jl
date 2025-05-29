```
fix_parameters(F::Union{System,AbstractSystem}, p; compile::Union{Bool,Symbol} = mixed)
```

Fix the parameters of the given system `F`. Returns a [`FixedParameterSystem`](@ref).
