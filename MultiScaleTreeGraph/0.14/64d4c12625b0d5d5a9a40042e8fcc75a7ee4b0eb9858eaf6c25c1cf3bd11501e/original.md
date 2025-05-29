```
nleaves(node)
nleaves!(node)
```

Get the total number of leaves a node is bearing, *i.e.* the number of terminal nodes. `nleaves!` is faster than `nleaves` but cache the results in a variable so it uses more memory. Please use [`clean_cache!`](@ref) after calling `nleaves!` to clean the temporary variables.

# Examples

```julia
# Importing the mtg from the github repo:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

nleaves!(mtg)

clean_cache!(mtg)
```
