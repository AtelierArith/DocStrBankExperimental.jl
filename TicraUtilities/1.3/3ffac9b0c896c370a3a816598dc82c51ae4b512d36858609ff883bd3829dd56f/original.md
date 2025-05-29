```
read_sphfile(fname) -> Vector{SPHQPartition}
```

Read the SPH coefficients from a Q-type spherical wave expansion file. 

In the process of reading the data, the coefficients in the file (Q′) are conjugated and then multiplied by the factor √(8π) to achieve Ticra-standard normalization.   Each element of the returned vector corresponds to a particular operating frequency partition in the file.  If there is only a single partition in the file, then instead of returning a 1-element vector, the single element of type `SPHQPartition` is returned as a scalar.
