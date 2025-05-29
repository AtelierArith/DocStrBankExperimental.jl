```
eta_uniformgrid = interpsurface(amrgrid::Vector{VisClaw.AMRGrid}, topo::VisClaw.Topo)
eta_uniformgrid = interpsurface(amr::VisClaw.AMR, topo::VisClaw.Topo)
```

Convert AMR tile data into uniform grid data using the SciPy scattered interpolation.

Interpolation of inundation height (land) is not supported. 
