```
npzwrite(filename::AbstractString, vars::Dict{<:AbstractString})
npzwrite(filename::AbstractString, args...; kwargs...)
```

In the first form, write the variables in `vars` to an `npz` file named `filename`.

In the second form, collect the variables in `args` and `kwargs` and write them all to `filename`. The variables in `args` are saved with names `arr_0`, `arr_1`  and so on, whereas the ones in `kwargs` are saved with the specified names.

Unlike `numpy`, the extension `.npz` is not appened to `filename`.

!!! warn "Warning"
    Any existing file with the same name will be overwritten.


# Examples

```julia
julia> npzwrite("temp.npz", Dict("x" => ones(3), "y" => 3))

julia> npzread("temp.npz")
Dict{String,Any} with 2 entries:
  "x" => [1.0, 1.0, 1.0]
  "y" => 3

julia> npzwrite("temp.npz", ones(2,2), x = ones(3), y = 3)

julia> npzread("temp.npz")
Dict{String,Any} with 3 entries:
  "arr_0" => [1.0 1.0; 1.0 1.0]
  "x"     => [1.0, 1.0, 1.0]
  "y"     => 3
```
