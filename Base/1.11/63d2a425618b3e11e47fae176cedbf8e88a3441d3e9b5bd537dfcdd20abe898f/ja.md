```
cumprod(A; dims::Integer)
```

次元 `dim` に沿った累積積。出力の精度を制御し（例えば、オーバーフローを避けるために）、パフォーマンスのために事前に割り当てられた出力配列を使用するには、[`cumprod!`](@ref) も参照してください。

# 例

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
