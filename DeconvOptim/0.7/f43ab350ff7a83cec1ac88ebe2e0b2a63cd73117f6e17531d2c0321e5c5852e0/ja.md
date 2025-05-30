```
generate_downsample(num_dim, downsample_dims, factor)
```

配列をダウンサンプリングするために使用できる関数を生成します（Tullio.jlに基づく）。`num_dim`（整数）は配列の次元です。`downsample_dims`はどの次元をダウンサンプリングするかのリストです。`factor`はダウンサンプリングファクターで、整数である必要があります。

# 例

```jldoctest
julia> ds = generate_downsample(2, [1, 2], 2) 
[...]
julia> ds([1 2; 3 4; 5 6; 7 8])
2×1 Array{Float64,2}:
 2.5
 6.5

julia> ds = generate_downsample(2, [1], 2)
[...]
julia> ds([1 2; 3 5; 5 6; 7 8])
2×2 Array{Float64,2}:
 2.0  3.5
 6.0  7.0
```
