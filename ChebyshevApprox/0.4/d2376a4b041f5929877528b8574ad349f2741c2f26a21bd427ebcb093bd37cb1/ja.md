`N` 個のタイプ `T` のポイントを `node_generator` に従って計算し、ポイントを `domain` で指定された区間にスケーリングします（デフォルトは [1.0,-1.0] です）。 ポイントは `node_generator` に従って構造体 (ChebRoots, ChebExtrema, ChebExtended) で返されます。

# シグネチャ

points = nodes(T,N,node_generator,domain)

# 例

```
julia> using DoubleFloats
julia> points = nodes(Double64,4,:chebyshev_nodes)
julia> points = nodes(Double64,4,:chebyshev_extrema)
julia> points = nodes(Double64,4,:chebyshev_extended)

julia> points = nodes(Double64,4,:chebyshev_nodes,[3.0,-1.0])
julia> points = nodes(Double64,4,:chebyshev_extrema,[3.0,-1.0])
julia> points = nodes(Double64,4,:chebyshev_extended,[3.0,-1.0])
```
