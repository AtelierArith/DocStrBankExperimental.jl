```
GConvGRU(args...; kws...)
```

[`GConvGRUCell`](@ref)セルに対応する再帰層を構築します。これは、ノード特徴の全時系列を一度に処理するために使用できます。

引数は[`GConvGRUCell`](@ref)コンストラクタに渡されます。詳細については[`GNNRecurrence`](@ref)を参照してください。

# 例

```jldoctest
julia> num_nodes, num_edges = 5, 10;

julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> g = rand_graph(num_nodes, num_edges);

julia> x = rand(Float32, d_in, timesteps, num_nodes);

julia> layer = GConvGRU(d_in => d_out, 2)
GConvGRU(
  GConvGRUCell(2 => 3, 2),              # 108 パラメータ
)                   # 合計: 12 配列, 108 パラメータ, 1.148 KiB.

julia> y = layer(g, x);

julia> size(y) # (d_out, timesteps, num_nodes)
(3, 5, 5)
```
