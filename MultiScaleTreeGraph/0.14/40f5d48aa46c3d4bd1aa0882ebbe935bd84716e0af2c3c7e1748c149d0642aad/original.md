```
select!(node::Node, args..., <keyword arguments>)
select(node::Node, args..., <keyword arguments>)
```

Delete all attributes not selected in `args...`, and optionally apply transformations on the fly on the selected variables. This function works similarly to [`transform!`](@ref) except it keeps only the selected variables, while [`transform!`](@ref) add new variables.

See the documentation of [`transform!`](@ref) for more details on the format of `args` and on how to use the arguments.

This function adds one more form to `args...`: a variable name to just select a variable.

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

select!(mtg, :Length => (x -> x / 10) => :length_m, :Width, ignore_nothing = true)
```
