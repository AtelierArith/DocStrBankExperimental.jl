```julia
vextrema(A; dims)
```

`A`の最大値と最小値を見つけます。オプションで、`dims`で指定された次元に沿って計算します。`Base.extrema`と同様ですが、ベクトル化されています。

## 例

julia> A = reshape(Vector(1:2:16), (2,2,2)) 2×2×2 Array{Int64, 3}:  [:, :, 1] =   1  5   3  7

[:, :, 2] =    9  13   11  15

julia> extrema(A, dims = (1,2)) 1×1×2 Array{Tuple{Int64, Int64}, 3}:  [:, :, 1] =   (1, 7)

[:, :, 2] =   (9, 15)
