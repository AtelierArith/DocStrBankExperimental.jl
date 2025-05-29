```
FeaturedGraph(g, [mt]; directed=:auto, nf, ef, gf, pf=nothing,
    T, N, E, with_batch=false)
```

ノード、エッジ、およびグラフ全体に関連する特徴を含む配列を格納するグラフ構造を表す型です。

`FeaturedGraph`は、グラフ内の接続を表す異なるオブジェクト`g`から構築できます。他のフィーチャーグラフ`fg`から構築されると、内部のグラフ表現は保持され、共有されます。

# 引数

  * `g`: グラフトポロジーを表すデータ。可能な型は

      * 隣接行列。
      * 隣接リスト。
      * Graphsのグラフ、すなわち`SimpleGraph`、`SimpleDiGraph`、またはSimpleWeightedGraphsの`SimpleWeightedGraph`、`SimpleWeightedDiGraph`。
      * `AbstractFeaturedGraph`オブジェクト。
  * `mt::Symbol`: 行列形式の`g`の行列タイプ。`graph`が行列形式の場合、`mt`は`:adjm`、`:normedadjm`、`:laplacian`、`:normalized`または`:scaled`のいずれかとして記録されます。
  * `directed`: グラフの方向を指定します。`:auto`、`:directed`、および`:undirected`のいずれかです。デフォルト値は`:auto`で、方向は自動的に推測されます。
  * `nf`: ノードの特徴。
  * `ef`: エッジの特徴。
  * `gf`: グローバルな特徴。
  * `pf`: 位置的特徴。`nothing`が指定された場合、位置エンコーディングはオフになります。配列が指定された場合、位置エンコーディングは指定された配列として割り当てられます。`:auto`が指定された場合、ノード特徴のために位置エンコーディングが自動的に生成され、`with_batch`が考慮されます。
  * `T`: グラフの要素型を指定します。デフォルト値は`g`の要素型です。
  * `N`: `g`のノード数。
  * `E`: `g`のエッジ数。
  * `with_batch::Bool`: すべての特徴の最後の次元をバッチ次元として考慮します。

# 使用法

```
using GraphSignals, CUDA

# 隣接リスト表現から構築
g = [[2,3], [1,4,5], [1], [2,5], [2,4]]
fg = FeaturedGraph(g)

# ノード数とエッジ数
nv(fg)  # 5
ne(fg)  # 10

# Graphsのグラフから
fg = FeaturedGraph(erdos_renyi(100, 20))

# ノード特徴を追加しながらフィーチャーグラフをコピー
fg = FeaturedGraph(fg, nf=rand(100, 5))

# GPUに送信
fg = fg |> cu
```

他にも[`graph`](@ref)、[`node_feature`](@ref)、[`edge_feature`](@ref)、および[`global_feature`](@ref)を参照してください。
