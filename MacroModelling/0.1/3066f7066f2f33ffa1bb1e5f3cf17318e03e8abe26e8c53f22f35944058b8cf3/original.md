```julia
write_mod_file(m)

```

Writes a `dynare` .mod-file in the current working directory. This function is not guaranteed to produce working code. It's purpose is to make it easier to port a model from `MacroModelling.jl` to `dynare`. 

The recommended workflow is to use this function to write a .mod-file, and then adapt the output so that it runs and corresponds to the input.

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
