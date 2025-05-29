```
traverse!(node::Node, f::Function[, args...], <keyword arguments>)
traverse(node::Node, f::Function[, args...], <keyword arguments>)
```

Traverse the nodes of a (sub-)tree, given any starting node in the tree, and apply a function which is either mutating (use `traverse!`) or not (use `traverse`).

# Arguments

  * `node::Node`: An MTG node (*e.g.* the whole mtg returned by `read_mtg()`).
  * `f::Function`: a function to apply over each node
  * `args::Any`: any argument to pass to the function
  * <keyword arguments>:

      * `scale = nothing`: The scale to filter-in (i.e. to keep). Usually a Tuple-alike of integers.
      * `symbol = nothing`: The symbol to filter-in. Usually a Tuple-alike of Strings.
      * `link = nothing`: The link with the previous node to filter-in. Usually a Tuple-alike of Char.
      * `filter_fun = nothing`: Any filtering function taking a node as input, e.g. [`isleaf`](@ref).
      * `all::Bool = true`: Return all filtered-in nodes (`true`), or stop at the first node that is filtered out (`false`).
      * `type::Type = Any`: The elements type of the returned array. This can speed-up things. Only available for the non-mutating version.
      * `recursivity_level::Int = Inf`: The maximum depth of the traversal. Default is `Inf` (*i.e.* no limit).

# Returns

`nothing` for `traverse!` because it mutates the (sub-)tree in-place, or an `Array{type}` (or `Array{Any}` if `type` is not given) for `traverse`.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
traverse!(mtg, node -> isleaf(node) ? println(node_id(node)," is a leaf") : nothing)
node_5 is a leaf
node_7 is a leaf

# We can also use the `do...end` block notation when we have a complex set of instructions:
traverse!(mtg) do node
    if isleaf(node)
         println(node_id(x)," is a leaf")
    end
end
```
