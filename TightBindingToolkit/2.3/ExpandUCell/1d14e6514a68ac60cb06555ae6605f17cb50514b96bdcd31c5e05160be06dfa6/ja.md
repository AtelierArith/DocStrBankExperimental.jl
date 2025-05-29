```julia
ExpandUnitCell(ucOG::UnitCell{T}, scaling::Vector{Int64} ; OffsetRange::Int64 = 2)
```

与えられた単位セルの整数倍の単位セルを返します（原始ベクトルは各方向に沿った与えられたスケーリングによってスケーリングされます）。結合は新しいサブ格子と新しい原始ベクトルの間で適切に再定義されます。
