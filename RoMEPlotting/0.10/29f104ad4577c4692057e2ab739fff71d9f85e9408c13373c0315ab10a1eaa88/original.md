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

Analyzing repeat solves is easier if you can animate repeat solves.

Notes

  * Repeat solves can be stored using `solveTree!(fg, storeOld=true)`.
  * Experimental, see DFG #641

Example

```julia
using Images, Caesar, RoMEPlotting

fg = generateGraph_Hexagonal()

for i in 1:10
  solveTree!(fg, storeOld=true)
end

# generate all the plots in RAM
plts = plotSLAM2DSolveKeys(fg)

# export all images to a video
imgs = convert.(Matrix{RGB},plts)
Caesar.writevideo("/tmp/test.avi", imgs)
@async run(`totem /tmp/test.avi`)
```

Related

writevideo, plotSolveKey, listSolveKeys
