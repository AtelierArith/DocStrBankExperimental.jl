```
getcoordinates!(x::Vector{<:Vec}, grid::AbstractGrid, idx::Union{Int,CellIndex})
getcoordinates!(x::Vector{<:Vec}, grid::AbstractGrid, cell::AbstractCell)
```

`x`を`idx`または`cell`に対応するセルの座標に変更します。
