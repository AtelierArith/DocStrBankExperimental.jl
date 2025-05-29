```
add_method_initialize!(reaction::AbstractReaction, method::AbstractReactionMethod)
add_method_initialize!(reaction::AbstractReaction, methodfn::Function, vars::Tuple{Vararg{AbstractVarList}}; kwargs...) -> ReactionMethod
```

Add or create-and-add an initialize method (called at start of each main loop iteration)  eg to zero out accumulator Variables. `methodfn`, `vars`, `kwargs` are passed to [`ReactionMethod`](@ref).
