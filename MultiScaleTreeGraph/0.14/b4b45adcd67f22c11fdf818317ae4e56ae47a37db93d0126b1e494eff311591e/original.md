```
@mutate_mtg!(node, args...,kwargs...)
```

Mutate the mtg nodes in place.

# Arguments

  * `mtg`: the mtg to mutate
  * `args...`: The computations to apply to the nodes (see examples)
  * `kwargs...`: Optional keyword arguments for traversing and filtering (see details)

# Details

As for [`descendants`](@ref) and [`ancestors`](@ref), kwargs can be any filter from:

  * `scale = nothing`: The scale to filter-in (i.e. to keep). Usually a Tuple-alike of integers.
  * `symbol = nothing`: The symbol to filter-in. Usually a Tuple-alike of Strings.
  * `link = nothing`: The link with the previous node to filter-in. Usually a Tuple-alike of Char.
  * `all::Bool = true`: Return all filtered-in nodes (`true`), or stop at the first node that

is filtered out (`false`).

  * `filter_fun = nothing`: Any filtering function taking a node as input, e.g. [`isleaf`](@ref).
  * `traversal`: The type of tree traversal. By default it is using `AbstractTrees.PreOrderDFS`.

# Examples

```julia
# Importing an mtg from the package:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# Compute a new attribute with the scales and add 2 to its values:
@mutate_mtg!(mtg, scaling = node.scales .+ 2, filter_fun = node -> node.scales !== nothing)

# Compute several new attributes, some based on others:
@mutate_mtg!(mtg, x = length(node_id(node)), y = node.x + 2, z = sum(node.y))

# We can also use it without parenthesis:

@mutate_mtg! mtg x = length(node_id(node))
```
