```
  cwd() -> SystemPath
```

Get the current working directory.

# Examples

```julia-repl
julia> cwd()
p"/home/JuliaUser"

julia> cd(p"/home/JuliaUser/Projects/julia")

julia> cwd()
p"/home/JuliaUser/Projects/julia"
```
