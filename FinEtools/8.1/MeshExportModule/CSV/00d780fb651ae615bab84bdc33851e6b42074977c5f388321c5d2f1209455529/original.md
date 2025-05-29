```
savecsv(name::String; kwargs...)
```

Save arrays as a CSV file.

Example:

```julia
savecsv("ab", a = rand(3), b = rand(3))
```
