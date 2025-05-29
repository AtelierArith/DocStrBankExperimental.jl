```julia
drawCliqSubgraphUpMocking(
    fgl,
    treel,
    frontalSym;
    show,
    filepath,
    engine,
    viewerapp
)

```

クリーク `frontalSym::Symbol` に関連するサブグラフを構築し、描画します。

ノート

  * キーワードオプションの詳細については `drawGraphCliq`/`writeGraphPdf` を参照してください。

関連

drawGraphCliq, spyCliqMat, drawTree, buildCliqSubgraphUp, buildSubgraphFromLabels!
