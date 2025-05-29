```
add_method_do!(reaction::AbstractReaction, method::AbstractReactionMethod)
add_method_do!(reaction::AbstractReaction, methodfn::Function, vars::Tuple{Vararg{AbstractVarList}}; kwargs...) -> ReactionMethod
```

Add or create and add a main loop method. `methodfn`, `vars`, `kwargs` are passed to [`ReactionMethod`](@ref).
