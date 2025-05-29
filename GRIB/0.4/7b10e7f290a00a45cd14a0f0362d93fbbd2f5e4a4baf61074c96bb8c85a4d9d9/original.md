```
GribFile(f::Function, filename::AbstractString, mode="rb")
```

Open a grib file and automatically close after exucuting `f`. `mode` is a mode as described by `Base.open`.

# Example

```julia
GribFile(filename) do f
    # do things in read mode
end
```
