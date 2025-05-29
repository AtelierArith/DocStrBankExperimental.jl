```julia
nodeflux(system, U)

```

Reconstruction of  edge flux as  vector function  on the nodes  of the triangulation.  The result  can be seen as a  piecewiesw linear vector function in the FEM space spanned by the discretization nodes exhibiting the flux density.  

The reconstruction is based on the  "magic formula" R. Eymard, T. Gallouet, R. Herbin, IMA Journal of Numerical Analysis (2006) 26, 326−353, Lemma 2.4 .

The return value is a `dim x nspec x nnodes` vector. The flux of species i can  e.g. plotted via GridVisualize.vectorplot.

Example:

```julia
    ispec=3
    vis=GridVisualizer(Plotter=Plotter)
    scalarplot!(vis,grid,solution[ispec,:],clear=true,colormap=:summer)
    vectorplot!(vis,grid,nf[:,ispec,:],clear=false)
    reveal(vis)
```

CAVEAT: there is a possible unsolved problem with the values at domain  corners in the code. Please see any potential boundary artifacts as a manifestation of this issue and report them.
