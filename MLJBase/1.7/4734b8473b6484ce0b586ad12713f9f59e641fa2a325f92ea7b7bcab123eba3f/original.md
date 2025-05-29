```
Node{T<:Union{Machine,Nothing}}
```

Type for nodes in a learning network that are not `Source` nodes.

The key components of a Node are:

  * An *operation*, which will either be static (a fixed function) or dynamic (such as `predict` or `transform`).
  * A `Machine` object, on which to dispatch the operation (`nothing` if the operation is static). The training arguments of the machine are generally other nodes, including `Source` nodes.
  * Upstream connections to other nodes, called its *arguments*, possibly including `Source` nodes, one for each data argument of the operation (typically there's just one).

When a node `N` is called, as in `N()`, it applies the operation on the machine (if there is one) together with the outcome of calls to its node arguments, to compute the return value. For details on a node's calling behavior, see [`node`](@ref).

See also [`node`](@ref), [`Source`](@ref), [`origins`](@ref), [`sources`](@ref), [`fit!`](@ref).
