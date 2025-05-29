```
eleid = addelement!(model,ElType,nodid;kwargs...)
```

Add one or several elements to `model`, connecting them to the nodes specified  by `nodid`.

If `nodid` is an `AbstractVector`: add a single element to the model. `eleid` is then a single element identifier.

If `nodid` is an `AbstractMatrix`: add multiple elements to the model. Each  row of `nodid` identifies the node of a single element. `eleid` is then  a vector of element identifiers.

For each element, `addelement!` will call `eleobj = ElType(nodes;kwargs...)` where `nodes` is a vector of nodes of the element.

See also: [`addnode!`](@ref), [`describe`](@ref), [`coord`](@ref)
