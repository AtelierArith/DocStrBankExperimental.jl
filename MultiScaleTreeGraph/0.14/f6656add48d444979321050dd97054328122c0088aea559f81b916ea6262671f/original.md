```
descendants(node::Node,key,<keyword arguments>)
descendants(node::Node,<keyword arguments>)
descendants!(node::Node,key,<keyword arguments>)
```

Get attribute values from the descendants of the node (acropetal). The first method returns an array of values, the second an array of nodes that respect the filters, and the third the mutating version of the  first one that caches the results in the mtg.

The mutating version (`descendants!`) cache the results in a cached variable named after the hash of the function call. This version is way faster when `descendants` is called repeateadly for the same computation on large trees, but require to clean the chache sometimes  (see [`clean_cache!`](@ref)). It also only works for trees with attributes of subtype of `AbstractDict`.

# Arguments

## Mandatory arguments

  * `node::Node`: The node to start at.
  * `key`: The key, or attribute name (only mandatory for the first and third methods). Make it a `Symbol` for faster computation time.

## Keyword Arguments

  * `scale = nothing`: The scale to filter-in (i.e. to keep). Usually a Tuple-alike of integers.
  * `symbol = nothing`: The symbol to filter-in. Usually a Tuple-alike of Strings.
  * `link = nothing`: The link with the previous node to filter-in. Usually a Tuple-alike of Char.
  * `all::Bool = true`: Return all filtered-in nodes (`true`), or stop at the first node that

is filtered out (`false`).

  * `self = false`: is the value for the current node needed ?
  * `filter_fun = nothing`: Any filtering function taking a node as input, e.g. [`isleaf`](@ref).
  * `recursivity_level = Inf`: The maximum number of recursions allowed (considering filters).

*E.g.* to get the first level children only: `recursivity_level = 1`, for children + grand-children: `recursivity_level = 2`. If `Inf` (the default) or a negative value is provided, there is no  recursion limitation.

  * `ignore_nothing = false`: filter-out the nodes with `nothing` values for the given `key`
  * `type::Union{Union,DataType}`: The type of the attribute. Can make the function run much

faster if provided (*e.g.* ≈4x faster).

# Tips

To get the values of the leaves use [`isleaf`](@ref) as the filtering function, e.g.: `descendants(mtg, :Width; filter_fun = isleaf)`.

# Note

In most cases, the `type` argument should be given as a union of `Nothing` and the data type of the attribute to manage missing or inexistant data, e.g. measurements made at one scale only. See examples for more details.

# Examples

```julia
# Importing the mtg from the github repo:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

descendants(mtg, :Length) # Short to write, but slower to execute

# Fast version, note that we pass a union of Nothing and Float64 because there are some nodes
# without a `Length` attribute:
descendants(mtg, :Length, type = Union{Nothing,Float64})

# Filter by scale:
descendants(mtg, :XEuler, scale = 3, type = Union{Nothing, Float64})
descendants(mtg, :Length, scale = 3, type = Float64) # No `nothing` value here, no need of a union type

# Filter by symbol:
descendants(mtg, :Length, symbol = "Leaf")
descendants(mtg, :Length, symbol = ("Leaf","Internode"))

# Filter by function, e.g. get the values for the leaves only:
descendants(mtg, :Width; filter_fun = isleaf)

# You can also ask for different attributes by passing them as a vector:
descendants(mtg, [:Width, :Length]; filter_fun = isleaf)
# The output is an array of arrays of length of the attributes you asked for.

# It is possible to cache the results in the mtg using the mutating version `descendants!` (note the `!` 
# at the end of the function name):
transform!(mtg, node -> sum(descendants!(node, :Length)) => :subtree_length, symbol = "Internode")

# Or using `@mutate_mtg!` instead of `transform!`:
@mutate_mtg!(mtg, subtree_length = sum(descendants!(node, :Length)), symbol = "Internode")

# The cache is stored in a temporary variable with a name that starts with `_cache_` followed by the SHA
# of the function call, *e.g.*: `:_cache_5c1e97a3af343ce623cbe83befc851092ca61c8d`:
node_attributes(mtg[1][1][1])

# You can then clean the cache to avoid using too much memory:
clean_cache!(mtg)
node_attributes(mtg[1][1][1])
```
