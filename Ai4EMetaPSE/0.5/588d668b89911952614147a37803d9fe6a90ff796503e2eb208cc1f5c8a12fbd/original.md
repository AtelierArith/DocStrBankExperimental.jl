```julia
json2julia(io::AbstractString) -> Any

```

json2julia converts a JSON string to a Julia expression.

# Examples:

```julia
file = joinpath(@__DIR__, "JsonFiles/julia2jsonTest1.json")
ex = json2julia(file)
```
