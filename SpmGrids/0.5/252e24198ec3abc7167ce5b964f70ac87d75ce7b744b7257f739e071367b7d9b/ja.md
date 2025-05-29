```
resize!(grid::SpmGrid, args...; kwargs...)
```

グリッドの次元をリサイズします。引数とキーワード引数は、[ImageTransformations.imresize](@ref) 関数と似ています。

例:

```julia
julia> resize!(grid, ratio=0.5)  # すべての次元を0.5の係数でリサイズ
julia> resize!(grid, ratio=(0.5, 0.5))  # xおよびy次元を0.5の係数でリサイズ
julia> resize!(grid, ratio=(0.5, 0.5, 2.0))  # xおよびy次元を0.5の係数でリサイズ、z次元を2の係数でリサイズ
julia> resize!(grid, 64, 64)    # xおよびy次元を特定のピクセルサイズにリサイズ
julia> resize!(grid, 32, 96, 128)   # すべての次元を特定のピクセルサイズにリサイズ
```
