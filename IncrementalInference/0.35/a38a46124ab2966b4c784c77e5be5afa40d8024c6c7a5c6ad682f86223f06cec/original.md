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

Construct (new) subgraph and draw the subgraph associated with clique `frontalSym::Symbol`.

Notes

  * See `drawGraphCliq`/`writeGraphPdf` for details on keyword options.

Related

drawGraphCliq, spyCliqMat, drawTree, buildCliqSubgraphUp, buildSubgraphFromLabels!
