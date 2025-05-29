```julia
translate_mod_file(path_to_mod_file)

```

Reads in a `dynare` .mod-file, adapts the syntax, tries to capture parameter definitions, and writes a julia file in the same folder containing the model equations and parameters in `MacroModelling.jl` syntax. This function is not guaranteed to produce working code. It's purpose is to make it easier to port a model from `dynare` to `MacroModelling.jl`. 

The recommended workflow is to use this function to translate a .mod-file, and then adapt the output so that it runs and corresponds to the input.

Note that this function copies the .mod-file to a temporary folder and executes it there. All references within that .mod-file are therefore not valid (because those filesare not copied) and must be made copied into the .mod-file.

# Arguments

  * `path_to_mod_file` [Type: `AbstractString`]: path including filename of the .mod-file to be translated
