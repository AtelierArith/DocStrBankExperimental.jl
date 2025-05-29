```
add_method_setup!(reaction::AbstractReaction, method::AbstractReactionMethod)
add_method_setup!(reaction::AbstractReaction, methodfn::Function, vars::Tuple{Vararg{AbstractVarList}}; kwargs...) -> ReactionMethod
```

Add or create-and-add a setup method (called before main loop) eg to set persistent data or initialize state variables. `methodfn`, `vars`, `kwargs` are passed to [`ReactionMethod`](@ref).
