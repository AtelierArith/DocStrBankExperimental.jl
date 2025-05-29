```
ConcreteFeaturedGraph(fg; nf=node_feature(fg), ef=edge_feature(fg),
                      gf=global_feature(fg), pf=positional_feature(fg))
```

これは`FeaturedGraph`および`FeaturedSubgraph`オブジェクトの構築のための構文糖です。これは冪等な操作であり、入力と同じタイプのオブジェクトを返します。入力`fg`を再ラップしますが、`kwargs`で再構成します。

# 引数

  * `fg`: `FeaturedGraph`および`FeaturedSubgraph`オブジェクト。
  * `nf`: ノード特徴。
  * `ef`: エッジ特徴。
  * `gf`: グローバル特徴。
  * `pf`: 位置信号。

# 使用法

```jldoctest
julia> using GraphSignals

julia> adjm = [0 1 1 1;
               1 0 1 0;
               1 1 0 1;
               1 0 1 0];

julia> nf = rand(10, 4);

julia> fg = FeaturedGraph(adjm; nf=nf)
FeaturedGraph:
	無向グラフ (#V=4, #E=5) の隣接行列
	ノード特徴:	ℝ^10 <Matrix{Float64}>

julia> ConcreteFeaturedGraph(fg, nf=rand(7, 4))
FeaturedGraph:
    無向グラフ (#V=4, #E=5) の隣接行列
    ノード特徴:	ℝ^7 <Matrix{Float64}>
```
