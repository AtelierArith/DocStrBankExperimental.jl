```
nodeflux(system, U; data)
```

Reconstruction of the edge flux as vector function  on the nodes  of the triangulation. See [`nodeflux(system,F,U;data)`](@ref).

The flux of species i can  e.g. plotted via GridVisualize.vectorplot.

Example:

```julia
    ispec=3
    vis=GridVisualizer(Plotter=Plotter)
    scalarplot!(vis,grid,solution[ispec,:],clear=true,colormap=:summer)
    vectorplot!(vis,grid,nf[:,ispec,:],clear=false)
    reveal(vis)
```
