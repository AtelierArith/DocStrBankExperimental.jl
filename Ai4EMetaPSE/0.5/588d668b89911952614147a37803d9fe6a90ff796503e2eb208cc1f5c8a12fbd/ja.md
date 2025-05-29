```julia
json2julia(io::AbstractString) -> Any

```

json2juliaはJSON文字列をJulia式に変換します。

# 例:

```julia
file = joinpath(@__DIR__, "JsonFiles/julia2jsonTest1.json")
ex = json2julia(file)
```
