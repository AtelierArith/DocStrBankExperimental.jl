```
LinkParameters(DM::AbstractDataModel, Linked::Union{AbstractVector{<:Bool},AbstractVector{<:Int}}, MainIndBefore::Int=findfirst(Linked); kwargs...)
```

Embeds the model such that all components `i` for which `Linked[i] == true` are linked to the parameter corresponding to component `MainIndBefore`. `Linked` can also be a `String`: this creates a `BitVector` whose components are `true` whenever the corresponding parameter name contains `Linked`.
