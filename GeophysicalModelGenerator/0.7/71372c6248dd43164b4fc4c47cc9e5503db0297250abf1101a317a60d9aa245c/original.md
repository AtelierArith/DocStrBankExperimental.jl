```
save_LaMEM_topography(Topo::CartData, filename::String)
```

This writes a topography file `Topo` for use in LaMEM, which should have size `(nx,ny,1)` and contain the field `:Topography`
