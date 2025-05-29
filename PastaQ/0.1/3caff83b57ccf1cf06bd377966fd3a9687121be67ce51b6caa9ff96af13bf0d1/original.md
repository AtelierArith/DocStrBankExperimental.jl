```
gatelayer(gatename::AbstractString, n::Int; kwargs...)
```

Create a uniform layer containing `n` identical quantum gates, idenfitied by `gatename`. If additional parameteres are provided, they are identically added to all gates.

```julia
gatelayer("H",3)
# 3-element Vector{Tuple{String, Int64}}:
#  ("H", 1)
#  ("H", 2)
#  ("H", 3)

gatelayer("X",1:2:5)
# 3-element Vector{Tuple{String, Int64}}:
#  ("X", 1)
#  ("X", 3)
#  ("X", 5)
```
