```julia
plotLocalProduct(
    fgl,
    lbl;
    solveKey,
    N,
    dims,
    levels,
    show,
    dirpath,
    mimetype,
    sidelength,
    title,
    xmin,
    xmax,
    ymin,
    ymax
)

```

隣接する因子から `lbl` への提案信念を因子グラフでプロットし（ベイジアンツリー表現は無視）、参照用に新しい積近似を表示します。

DevNotes

  * TODO、::MIME="image/svg" に標準化する、JuliaRobotics/DistributedFactorGraphs.jl#640 を参照してください。
