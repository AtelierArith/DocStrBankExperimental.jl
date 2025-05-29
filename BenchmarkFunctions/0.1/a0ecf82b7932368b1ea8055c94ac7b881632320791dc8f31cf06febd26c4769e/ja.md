```
ndgrid(grids...)
```

`grids` に沿った n 次元グリッドを作成します – 各次元に沿った反復可能なオブジェクトです。

# 例

```jldoctest
julia> ndgrid(0:1)
2-element Array{Tuple{Int64},1}:
 (0,)
 (1,)
```

`jldoctest julia> ndgrid((0:1,0:1)) 4-element Array{Tuple{Int64,Int64},1}:  (0, 0)  (1, 0)  (0, 1)  (1, 1)`
