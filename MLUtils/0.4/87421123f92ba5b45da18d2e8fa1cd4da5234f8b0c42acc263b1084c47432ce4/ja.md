```
randn_like([rng=default_rng()], x, [element_type=eltype(x)], [dims=size(x)])
```

与えられた要素型とサイズに基づいて、指定されたソース配列 `x` に基づいて配列を作成します。新しい配列のすべての要素は、正規分布から引き出されたランダムな値に設定されます。最後の2つの引数はどちらもオプションで、指定された配列の eltype とサイズにデフォルト設定されます。次元は整数またはタプル引数として指定できます。

デフォルトの乱数生成器が使用されますが、最初の引数として明示的にカスタムのものが渡された場合はそれが使用されます。

`Base.randn` および [`rand_like`](@ref) も参照してください。

# 例

```julia-repl
julia> x = ones(Float32, 2)
2-element Vector{Float32}:
 1.0
 1.0

julia> randn_like(x, (3, 3))
3×3 Matrix{Float32}:
 -0.385331    0.956231   0.0745102
  1.43756    -0.967328   2.06311
  0.0482372   1.78728   -0.902547

julia> using CUDA

julia> CUDA.ones(2, 2)
2×2 CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}:
 1.0  1.0
 1.0  1.0

julia> randn_like(x, Float64)
2×2 CuArray{Float64, 2, CUDA.Mem.DeviceBuffer}:
 -0.578527   0.823445
 -1.01338   -0.612053
```
