```
FeaturedSubgraph(fg, nodes)
```

`FeaturedGraph`上に軽量なサブグラフを構築します。

# 引数

  * `fg::AbstractFeaturedGraph`: サブグラフを構築するための基本となるフィーチャーグラフ。
  * `nodes::AbstractVector`: `fg`から予約するノードを指定します。

# 使用法

```
julia> using GraphSignals

julia> g = [[2,3], [1,4,5], [1], [2,5], [2,4]];

julia> fg = FeaturedGraph(g)
FeaturedGraph:
	隣接行列における無向グラフ (#V=5, #E=5)

julia> subgraph(fg, [1,2,3])
FeaturedGraph:
	隣接行列における無向グラフ (#V=5, #E=5)
	サブグラフ:	ノード([1, 2, 3])
```

構文糖については[`subgraph`](@ref)を参照してください。
