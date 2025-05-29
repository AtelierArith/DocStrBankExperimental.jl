```
gatelayer(gatename::AbstractString, bonds::Vector{Vector{Int}}; kwargs...)
```

一連の `bonds` に対して多量子ビットゲートの均一な層を作成します。

```julia
gatelayer("CX", [(j,j+1), j=1:2:5])
# 3-element Vector{Tuple{String, Tuple{Int64, Int64}}}:
#  ("CX", (1, 2))
#  ("CX", (3, 4))
#  ("CX", (5, 6))
```
