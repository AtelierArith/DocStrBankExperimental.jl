```
treemap(f, node)
```

Apply the function `f` to every node in the tree with root `node`, where `f` is a function that returns `(v, ch)` where `v` is a new value for the node (i.e. as returned by [`nodevalue`](@ref) and `ch` is the new children of the node. `f` will be called recursively so that all the children returned by `f` for a parent node will again be called for each child.  This means that to maintain the structure of a tree but merely map to new values, one should define `f = node -> (g(node), children(node))` for some function `g` which returns a value for the node.

The nodes of the output tree will all be represented by [`MapNode`](@ref) objects wrapping the returned values. This is necessary in order to guarantee that the output types can describe any tree topology.

Note that in most common cases tree nodes are of a type which depends on their connectedness and the function `f` should take this into account.  For example the tree `[1, [2, 3]]` contains integer leaves but two `Vector` nodes.  Therefore, the `f` in `treemap(f, [1, [2,3]])` must be a function that is valid for either `Int` or `Vector`.  Alternatively, to only operate on leaves do `map(𝒻, Leaves(itr))`.

It's very easy to write an `f` that makes `treemap` stack-overflow.  To avoid this, ensure that `f` eventually terminates, i.e. that sometimes it returns empty `children`.  For example, if `f(n) = (nothing, [0; children(n)])` will stack-overflow because every node will have at least 1 child.

To create a tree with [`HasNodeType`](@ref) which enables efficient iteration, see [`StableNode`](@ref) instead.

## Examples

```julia
julia> t = [1, [2, 3]];

julia> f(n) = n isa AbstractArray ? (nothing, children(n)) : (n+1, children(n))

julia> treemap(f, t)
nothing
├─ 2
└─ nothing
   ├─ 3
   └─ 4

julia> g(n) = isempty(children(n)) ? (nodevalue(n), []) : (nodevalue(n), [0; children(n)])
g (generic function with 1 method)

julia> treemap(g, t)
Any[1, [2, 3]]
├─ 0
├─ 1
└─ [2, 3]
   ├─ 0
   ├─ 2
   └─ 3
```
