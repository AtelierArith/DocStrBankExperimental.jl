```
ones_like(x, [element_type=eltype(x)], [dims=size(x)]))
```

与えられたソース配列 `x` に基づいて、指定された要素型とサイズの配列を作成します。新しい配列のすべての要素は 1 に設定されます。第二引数と第三引数はどちらもオプションで、与えられた配列の eltype とサイズがデフォルトになります。次元は整数またはタプル引数として指定できます。

関連情報として [`zeros_like`](@ref) と [`fill_like`](@ref) を参照してください。

# 例

```julia-repl
julia> x = rand(Float32, 2)
2-element Vector{Float32}:
 0.8621633
 0.5158395

julia> ones_like(x, (3, 3))
3×3 Matrix{Float32}:
 1.0  1.0  1.0
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> using CUDA

julia> x = CUDA.rand(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 0.82297   0.656143
 0.701828  0.391335

julia> ones_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0
 1.0  1.0
```
