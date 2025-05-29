```julia
plotSLAM2DSolveKeys(dfg; ...)
plotSLAM2DSolveKeys(
    dfg,
    pattern;
    xmin,
    xmax,
    ymin,
    ymax,
    contour
)

```

繰り返し解をアニメーション化できると、繰り返し解の分析が容易になります。

ノート

  * 繰り返し解は `solveTree!(fg, storeOld=true)` を使用して保存できます。
  * 実験的、DFG #641を参照

例

```julia
using Images, Caesar, RoMEPlotting

fg = generateGraph_Hexagonal()

for i in 1:10
  solveTree!(fg, storeOld=true)
end

# RAMにすべてのプロットを生成
plts = plotSLAM2DSolveKeys(fg)

# すべての画像を動画にエクスポート
imgs = convert.(Matrix{RGB},plts)
Caesar.writevideo("/tmp/test.avi", imgs)
@async run(`totem /tmp/test.avi`)
```

関連

writevideo, plotSolveKey, listSolveKeys
