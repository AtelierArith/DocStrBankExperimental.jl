```
service_of_type(agent, type::Type{T}, default=nothing)::Union{T,Nothing} where {T}
```

Return the current agent service of the type `type`. 

If a default is set, this default service will be added to the agent as service of te type `type. The function is especially useful if you want to extend the functionality of the agent without having to change the internals of the agent, as this functions enables the user to add  arbitrary data to the agent on which functions can be defined.
