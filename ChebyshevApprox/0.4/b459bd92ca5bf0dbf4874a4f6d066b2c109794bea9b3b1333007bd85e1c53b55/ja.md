`N` 個の点を `node_generator` に従って計算し、`domain` で指定された区間にスケーリングします（デフォルトは [1.0,-1.0]）。点を `node_generator` に応じて構造体 (ChebRoots, ChebExtrema, ChebExtended) で返します。

# シグネチャ

points = nodes(N,node_generator,domain)

# 例

```
julia> points = nodes(4,:chebyshev_nodes)
julia> points = nodes(4,:chebyshev_extrema)
julia> points = nodes(4,:chebyshev_extended)

julia> points = nodes(4,:chebyshev_nodes,[3.0,-1.0])
julia> points = nodes(4,:chebyshev_extrema,[3.0,-1.0])
julia> points = nodes(4,:chebyshev_extended,[3.0,-1.0])
```
