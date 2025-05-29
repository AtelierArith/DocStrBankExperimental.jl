```
npzread(filename::AbstractString, [vars])
```

Read a variable or a collection of variables from `filename`.  The input needs to be either an `npy` or an `npz` file. The optional argument `vars` is used only for `npz` files. If it is specified, only the matching variables are read in from the file.

!!! note "Zero-dimensional arrays"
    Zero-dimensional arrays are stripped while being read in, and the values that they contain are returned. This is a notable difference from numpy, where  numerical values are written out and read back in as zero-dimensional arrays.


# Examples

```julia
julia> npzwrite("temp.npz", x = ones(3), y = 3)

julia> npzread("temp.npz") # Reads all variables
Dict{String,Any} with 2 entries:
  "x" => [1.0, 1.0, 1.0]
  "y" => 3

julia> npzread("temp.npz", ["x"]) # Reads only "x"
Dict{String,Array{Float64,1}} with 1 entry:
  "x" => [1.0, 1.0, 1.0]
```
