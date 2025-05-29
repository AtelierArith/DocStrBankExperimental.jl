```
SplitAxes(axs::NTuple{N,AbstractUnitRange}, n::Real)
```

`axs`を`ceil(Int, n)`個のほぼ等しいサイズのチャンクに分割します。これは`axs`で表される最終次元に沿って行われます。

詳細については[`SplitAxis`](@ref)を参照してください。

# 例

```jldoctest; setup=:(using TiledIteration)
julia> A = rand(3, 16);

julia> collect(SplitAxes(axes(A), 4))
4-element Vector{Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 (1:3, 1:4)
 (1:3, 5:8)
 (1:3, 9:12)
 (1:3, 13:16)
```
