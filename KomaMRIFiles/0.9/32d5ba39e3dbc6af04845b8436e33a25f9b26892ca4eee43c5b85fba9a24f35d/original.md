```
obj = read_phantom_MRiLab(filename)
```

Returns the Phantom struct from a MRiLab phantom file `.mat`.

# Arguments

  * `filename`: (`::String`) the absolute or relative path of the phantom file `.mat`

# Returns

  * `obj`: (`::Phantom`) Phantom struct

# Examples

```julia-repl
julia> obj_file = joinpath(dirname(pathof(KomaMRI)), "../examples/2.phantoms/brain.mat")

julia> obj = read_phantom_MRiLab(obj_file)

julia> plot_phantom_map(obj, :ρ)
```
