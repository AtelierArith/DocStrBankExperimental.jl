```
rect!(grid,maskmin,maskmax; 
      region=1, 
      bregion=1, 
      bregions=nothing, 
      tol=1.0e-10)
```

Place a rectangle into a rectangular grid. It places a cellmask according to `maskmin` and `maskmax`, and introduces boundary faces via `bfacesmask! at all sides of the mask area. It is checked that the coordinate values in the mask match (with tolerance) corresponding directional coordinates of the grid.

If `bregions` is given it is assumed to be a vector corresponding to the number of sides, im the sequence `w,e` in 1D. `s,e,n,w` in 2D and `s,e,n,w,b,t` in 3D.

`bregion` or elements of `bregions` can be numbers or functions `ireg(current_region)`.

Examples: [Subgrid-from-rectangle](@ref), [Rect2d-with-bregion-function](@ref),  [Cross3d](@ref)
