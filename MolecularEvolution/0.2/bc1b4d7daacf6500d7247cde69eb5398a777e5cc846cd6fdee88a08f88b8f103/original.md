```
branchlength_update!(bl_modifier::UnivariateModifier, tree::FelNode, models; <keyword arguments>)
```

A more general version of [`branchlength_optim!`](@ref). Here `bl_modifier` can be either an optimizer or a sampler (or more generally, a UnivariateModifier).

# Keyword Arguments

See [`branchlength_optim!`](@ref).

!!! note
    `bl_modifier` is a positional argument here, and not a keyword argument.

