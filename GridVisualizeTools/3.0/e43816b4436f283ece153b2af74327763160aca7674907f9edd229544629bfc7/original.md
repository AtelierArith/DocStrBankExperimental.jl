```julia
extract_visible_cells3D(
    coord,
    cellnodes,
    cellregions,
    nregions,
    xyzcut;
    primepoints,
    Tp,
    Tf
)

```

Extract visible tetrahedra - those intersecting with the planes `x=xyzcut[1]` or `y=xyzcut[2]`  or `z=xyzcut[3]`. 

Return corresponding points and facets for each region for drawing as mesh (Makie,MeshCat) or trisurf (pyplot)
