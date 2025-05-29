```julia
plotPose(, pp; ...)
plotPose(
    ,
    pp,
    title;
    levels,
    c,
    legend,
    axis,
    scale,
    overlay,
    hdl
)

```

ポーズ信念を視覚的に意味のある多様体上の等高線情報としてプロットします。

例:

```julia
fg = generateGraph_ZeroPose()
initAll!(fg);
plotPose(fg, :x0)
```

関連

[`plotSLAM2D`](@ref), [`plotSLAM2DPoses`](@ref), [`plotBelief`](@ref), `plotKDECircular`
