```julia
edgevelocities(grid, velofunc; kwargs...)

```

グリッドのエッジに速度を投影します。つまり、与えられた `velofunc` のパス積分を、[`integrate`](@ref) によって提供されるボロノイセルのエッジに沿って計算します。
