```julia
generateGraph_Circle(; ...)
generateGraph_Circle(
    poses;
    fg,
    offsetPoses,
    autoinit,
    graphinit,
    landmark,
    loopClosure,
    stopEarly,
    biasTurn,
    kappaOdo,
    cyclePoses
)

```

円形パターンで1つのランドマークを持つ標準的なファクターグラフを生成します。

ノート

  * ポーズ、:x0, :x1,... Pose2,
  * オドメトリ、:x0x1f1, など、Pose2Pose2 (ガウス)
  * オプション: 1 ランドマーク、:l1, Point2,
  * 2つの観測、:x0l1f1, :x6l1f1, RangeBearing (ガウス)

例

```julia
using RoME

fg = generateGraph_Hexagonal()
drawGraph(fg, show=true)
```

開発ノート

  * TODO 新しい `calcHelix_T` を使用するようにリファクタリング。

関連

[`generateGraph_Circle`](@ref), [`generateGraph_Kaess`](@ref), [`generateGraph_TwoPoseOdo`](@ref)
