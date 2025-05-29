```
cbct_back(proj, rg, ig)
```

Cone-beam backprojector for feldkamp.jl

# in

  * `proj (ns,nt,na)` cone-beam projection views
  * `rg::CtGeom`
  * `ig::ImageGeom`

# out

  * `img (nx,ny,nz)` back-projection result
