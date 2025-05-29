```
write_mtg(file, mtg; kwargs...)
write_mtg(file, mtg, classes, description, features)
```

Write an mtg file to disk.

# Arguments

  * `file::String`: The path to the MTG file to write.
  * `mtg`: the mtg
  * `classes`: the classes section
  * `description`: the description section
  * `features`: the features section

# Note

kwargs can be used to give zero, one or two of the classes, description and features instead of all. In this case the missing ones are recomputed using [`get_classes`](@ref), [`get_features`](@ref) or [`get_description`](@ref).

# Examples

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)
write_mtg("test.mtg",mtg)
```
