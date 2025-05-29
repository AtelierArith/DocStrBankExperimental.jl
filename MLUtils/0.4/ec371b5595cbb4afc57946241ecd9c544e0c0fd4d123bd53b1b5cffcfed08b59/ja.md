```
rand_like([rng=default_rng()], x, [element_type=eltype(x)], [dims=size(x)])
```

与えられた要素タイプとサイズに基づいて、指定されたソース配列 `x` に基づいて配列を作成します。新しい配列のすべての要素はランダムな値に設定されます。最後の2つの引数はどちらもオプションで、指定された配列の eltype とサイズにデフォルト設定されます。次元は整数またはタプル引数として指定できます。

カスタムの乱数生成器が最初の引数として明示的に渡されない限り、デフォルトの乱数生成器が使用されます。

`Base.rand` および [`randn_like`](@ref) も参照してください。

# 例

```julia-repl
julia> x = ones(Float32, 2)
2-element Vector{Float32}:
 1.0
 1.0

julia> rand_like(x, (3, 3))
3×3 Matrix{Float32}:
 0.780032  0.920552  0.53689
 0.121451  0.741334  0.5449
 0.55348   0.138136  0.556404

julia> using CUDA

julia> CUDA.ones(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0
 1.0  1.0

julia> rand_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 0.429274  0.135379
 0.718895  0.0098756
```
