```julia
generateGraph_Hexagonal(
;
    fg,
    landmark,
    loopClosure,
    N,
    autoinit,
    graphinit
)

```

標準的なファクターグラフを生成します：ランドマーク1つを持つ六角形の円形パターンでの運転。

ノート

  * 7つのポーズ、:x0-:x6, Pose2,
  * 1つのランドマーク、:l1, Point2,
  * 6つのオドメトリ、:x0x1f1, など、Pose2Pose2 (ガウス)
  * 2つの視認、:x0l1f1, :x6l1f1, RangeBearing (ガウス)

例

```julia
using RoME

fg = generateGraph_Hexagonal()
drawGraph(fg, show=true)
```

関連

[`generateGraph_Circle`](@ref), [`generateGraph_Kaess`](@ref), [`generateGraph_TwoPoseOdo`](@ref), [`generateGraph_Boxes2D!`](@ref)
