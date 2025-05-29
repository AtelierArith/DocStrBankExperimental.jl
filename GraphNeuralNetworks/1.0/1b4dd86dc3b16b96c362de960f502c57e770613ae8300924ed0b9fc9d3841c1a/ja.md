```
EvolveGCNO(args...; kws...)
```

[`EvolveGCNOCell`](@ref)セルに対応する再帰層を構築します。これは、グラフとノード特徴の時間的なシーケンス全体を一度に処理するために使用できます。

引数は[`EvolveGCNOCell`](@ref)コンストラクタに渡されます。詳細については[`GNNRecurrence`](@ref)を参照してください。

# 例

```jldoctest
julia> d_in, d_out = 2, 3;

julia> timesteps = 5;

julia> num_nodes = [10, 10, 10, 10, 10];

julia> num_edges = [10, 12, 14, 16, 18];

julia> snapshots = [rand_graph(n, m) for (n, m) in zip(num_nodes, num_edges)];

julia> tg = TemporalSnapshotsGNNGraph(snapshots)

julia> x = [rand(Float32, d_in, n) for n in num_nodes];

julia> cell = EvolveGCNO(d_in => d_out)
GNNRecurrence(
  EvolveGCNOCell(2 => 3),               # 321 parameters
)                   # Total: 5 arrays, 321 parameters, 1.535 KiB.

julia> y = layer(tg, x);

julia> length(y)    # timesteps
5 

julia> size(y[end]) # (d_out, num_nodes[end])
(3, 10)
```
