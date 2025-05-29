```
add_lonlat!(df::DataFrame,XC,YC,func::Function)
```

Add lon & lat to dataframe using "exchanged" XC, YC after updating  subdomain indices (via func) if needed (MeshArrays.location*is*out)
