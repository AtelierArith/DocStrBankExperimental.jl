```julia
plotSLAM2D(
    fgl;
    solveKey,
    from,
    to,
    minnei,
    meanmax,
    posesPPE,
    landmsPPE,
    recalcPPEs,
    lbls,
    scale,
    x_off,
    y_off,
    drawTriads,
    dyadScale,
    levels,
    drawhist,
    MM,
    xmin,
    xmax,
    ymin,
    ymax,
    showmm,
    window,
    point_size,
    line_width,
    regexLandmark,
    regexPoses,
    variableList,
    manualColor,
    drawPoints,
    pointsColor,
    drawContour,
    drawEllipse,
    ellipseColor,
    title,
    aspect_ratio
)

```

因子グラフに含まれるポーズとランドマークの2Dプロット。ポーズとランドマークはそれぞれ `:x1, :x2, ...` および `:l0, :l1, ...` とラベル付けされていると仮定します。含める数の範囲は、`from` と `to` およびプロットを操作するための他のキーワード機能で制御できます。

ノート

  * ランドマークには `:l1`, `:l2`, ... を仮定します –
  * デフォルトのGadflyプロットサイズを増やすことができます（ブラウザのJSSVG用）： `Gadfly.set_default_plot_size(35cm,20cm)`。
  * キーワード `drawEllipse=true` を使用して、共分散エリプスなどの機能を有効または無効にできます。

DevNotes

  * TODO `tags=[:LANDMARK]` を使用するように更新
  * TODO `drawHist` を修正
  * TODO `showmm`, `spscale` を非推奨にする。

例:

```julia
fg = generateGraph_Hexagonal()
plotSLAM2D(fg)
plotSLAM2D(fg, drawPoints=false)
plotSLAM2D(fg, contour=false, drawEllipse=true)
plotSLAM2D(fg, contour=false, title="SLAM result 1")

# または因子グラフをロード
fg_ = loadDFG("somewhere.tar.gz")
plotSLAM2D(fg_)
```

関連

[`plotSLAM2DPoses`](@ref), [`plotSLAM2DLandmarks`](@ref), [`plotPose`](@ref), [`plotBelief`](@ref) 
