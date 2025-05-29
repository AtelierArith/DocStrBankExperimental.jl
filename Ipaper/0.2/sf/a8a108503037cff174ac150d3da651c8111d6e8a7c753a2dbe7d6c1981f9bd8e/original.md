```
merge_var(fs; vars=nothing, var=nothing,
    progress=true, box::Union{bbox,Nothing}=nothing)
```

# Arguments

  * `fs`: tiff file paths
  * `vars`: variables in the tiff
  * `var`: variable to merge

# Examples

```julia
box = bbox(-180, -60, 180, 90)
```
