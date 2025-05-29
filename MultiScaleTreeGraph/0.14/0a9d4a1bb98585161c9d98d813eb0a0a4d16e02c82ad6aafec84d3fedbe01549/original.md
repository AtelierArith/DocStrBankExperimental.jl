```
ancestors(node::Node,key,<keyword arguments>)
ancestors(node::Node,<keyword arguments>)
```

Get attribute values from the ancestors (basipetal), or the ancestor nodes that are not filtered-out.

# Arguments

## Mandatory arguments

  * `node::Node`: The node to start at.
  * `key`: The key, or attribute name. It is only mandatory for the first method that search for attributes values. The second method returns the node directly.

Make it a `Symbol` for faster computation time.

## Keyword Arguments

  * `scale = nothing`: The scale to filter-in (i.e. to keep). Usually a Tuple-alike of integers.
  * `symbol = nothing`: The symbol to filter-in. Usually a Tuple-alike of Strings.
  * `link = nothing`: The link with the previous node to filter-in. Usually a Tuple-alike of Char.
  * `all::Bool = true`: Return all filtered-in nodes (`true`), or stop at the first node that

is filtered out (`false`).

  * `self = false`: is the value for the current node needed ?
  * `filter_fun = nothing`: Any filtering function taking a node as input, e.g. [`isleaf`](@ref).
  * `recursivity_level = -1`: The maximum number of recursions allowed (considering filters).

*E.g.* to get the parent only: `recursivity_level = 1`, for parent + grand-parent: `recursivity_level = 2`. If a negative value is provided (the default), the function returns all valid values from the node to the root.

  * `ignore_nothing = false`: filter-out the nodes with `nothing` values for the given `key`
  * `type::Union{Union,DataType}`: The type of the attribute. Makes the function run much

faster if provided (≈4x faster).

# Note

In most cases, the `type` argument should be given as a union of `Nothing` and the data type of the attribute to manage missing or inexistant data, e.g. measurements made at one scale only. See examples for more details.

# Examples

```julia
# Importing an example mtg from the package:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# Using a leaf node from the mtg:
leaf_node = get_node(mtg, 5)

ancestors(leaf_node, :Length) # Short to write, but slower to execute

# Fast version, note that we pass a union of Nothing and Float64 because there are some nodes
# without a `Length` attribute:
ancestors(leaf_node, :Length, type = Union{Nothing,Float64})

# Filter by scale:
ancestors(leaf_node, :XX, scale = 1, type = Float64)
ancestors(leaf_node, :Length, scale = 3, type = Float64)

# Filter by symbol:
ancestors(leaf_node, :Length, symbol = "Internode")
ancestors(leaf_node, :Length, symbol = ("Axis","Internode"))
```
