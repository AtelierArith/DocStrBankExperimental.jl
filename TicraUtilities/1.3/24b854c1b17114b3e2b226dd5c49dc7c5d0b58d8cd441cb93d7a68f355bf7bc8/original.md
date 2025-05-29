```
write_sphfile(fname, qs::Vector{SPHQPartition})
write_sphfile(fname, qs::SPHQPartition)
```

Write SPH coefficients to a Q-type spherical wave expansion file.

Prior to writing the data into the file, the input coefficients (Q) are conjugated and then multiplied by the factor 1/sqrt(8π) to become Q′ and achieve consistency with Ticra-standard normalization.  
