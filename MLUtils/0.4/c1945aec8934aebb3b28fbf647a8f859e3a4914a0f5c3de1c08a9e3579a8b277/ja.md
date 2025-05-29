```
zeros_like(x, [element_type=eltype(x)], [dims=size(x)]))
```

与えられたソース配列 `x` に基づいて、指定された要素型とサイズの配列を作成します。新しい配列のすべての要素は0に設定されます。第二引数と第三引数はどちらもオプションで、与えられた配列のeltypeとサイズがデフォルトになります。次元は整数またはタプル引数として指定できます。

関連項目として [`ones_like`](@ref) と [`fill_like`](@ref) を参照してください。

# 例

```julia-repl
julia> x = rand(Float32, 2)
2-element Vector{Float32}:
 0.4005432
 0.36934233

julia> zeros_like(x, (3, 3))
3×3 Matrix{Float32}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> using CUDA

julia> x = CUDA.rand(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 0.0695155  0.667979
 0.558468   0.59903

julia> zeros_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 0.0  0.0
 0.0  0.0
```
