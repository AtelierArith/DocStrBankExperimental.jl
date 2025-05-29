```
nodeflux(system, U; data)
```

三角形分割のノード上でのベクトル関数としてのエッジフラックスの再構成。[`nodeflux(system,F,U;data)`](@ref)を参照してください。

種iのフラックスは、例えばGridVisualize.vectorplotを介してプロットできます。

例:

```julia
    ispec=3
    vis=GridVisualizer(Plotter=Plotter)
    scalarplot!(vis,grid,solution[ispec,:],clear=true,colormap=:summer)
    vectorplot!(vis,grid,nf[:,ispec,:],clear=false)
    reveal(vis)
```
