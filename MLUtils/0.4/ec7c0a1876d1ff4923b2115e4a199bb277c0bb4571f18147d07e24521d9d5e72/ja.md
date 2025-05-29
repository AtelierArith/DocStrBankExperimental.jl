```
fill_like(x, val, [element_type=eltype(x)], [dims=size(x)]))
```

与えられたソース配列 `x` に基づいて、指定された要素タイプとサイズの配列を作成します。新しい配列のすべての要素は `val` に設定されます。第三および第四の引数はどちらもオプションで、デフォルトでは指定された配列の eltype とサイズになります。次元は整数またはタプル引数として指定できます。

関連情報として [`zeros_like`](@ref) および [`ones_like`](@ref) を参照してください。

# 例

```julia-repl
julia> x = rand(Float32, 2)
2-element Vector{Float32}:
 0.16087806
 0.89916044

julia> fill_like(x, 1.7, (3, 3))
3×3 Matrix{Float32}:
 1.7  1.7  1.7
 1.7  1.7  1.7
 1.7  1.7  1.7

julia> using CUDA

julia> x = CUDA.rand(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 0.803167  0.476101
 0.303041  0.317581

julia> fill_like(x, 1.7, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 1.7  1.7
 1.7  1.7
```
