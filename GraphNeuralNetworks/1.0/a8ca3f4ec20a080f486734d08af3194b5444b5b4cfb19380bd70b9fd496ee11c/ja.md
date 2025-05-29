```
DotDecoder()
```

与えられた入力グラフ `g` とノード特徴 `x` に対して、各エッジでのドット積 `x_i ⋅ xj` を返すグラフニューラルネットワーク層です。

# 例

```jldoctest
julia> g = rand_graph(5, 6)
GNNGraph:
    num_nodes = 5
    num_edges = 6

julia> dotdec = DotDecoder()
DotDecoder()

julia> dotdec(g, rand(2, 5))
1×6 Matrix{Float64}:
 0.345098  0.458305  0.106353  0.345098  0.458305  0.106353
```
