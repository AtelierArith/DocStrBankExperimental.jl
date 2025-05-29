```julia
extract_visible_bfaces3D(
    coord,
    bfacenodes,
    bfaceregions,
    nbregions,
    xyzcut;
    primepoints,
    Tp,
    Tf
)

```

Extract visible boundary faces - those not cut off by the planes `x=xyzcut[1]` or `y=xyzcut[2]`  or `z=xyzcut[3]`. 

Return corresponding points and facets for each region for drawing as mesh (Makie,MeshCat) or trisurf (pyplot)
