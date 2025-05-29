```julia
plotSLAM2DPoses(
    fg;
    solveKey,
    regexPoses,
    from,
    to,
    variableList,
    meanmax,
    ppe,
    recalcPPEs,
    lbls,
    scale,
    x_off,
    y_off,
    drawhist,
    spscale,
    dyadScale,
    drawTriads,
    drawContour,
    levels,
    contour,
    line_width,
    drawPoints,
    pointsColor,
    drawEllipse,
    ellipseColor,
    manualColor
)

```

すべてのポーズの2Dプロット。ポーズは``::Symbol`型`:x0, :x1, ..., :xn`からラベル付けされていると仮定します。`to`と`from`を使用して描画される数`n`の範囲を制限します。基になるヒストグラムは有効または無効にでき、最大点の信念推定カーソルのサイズは`spscale`で制御できます。

将来:

  * ユーザー定義のポーズラベリングスキームに緩和します。例えば`:p1, :p2, ...`
