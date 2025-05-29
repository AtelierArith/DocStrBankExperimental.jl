```julia
RayBasis3DRCNNCal(r, xyz; showarrivals, xₒ)

```

Predict acoustic field at location `xyz` using `RayBasis3DRCNN` model. Set `showarrivals` to `true` to return an array of individual complex arrivals. `xₒ` is the reference location and can be an arbitrary location.
