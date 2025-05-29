The na_recode function also works on datacubes.  

```julia
na_recode(radiance_datacube, ncfobs_datacube)
```

Wherever the number of cloud-free observations is 0, radiance will be marked as missing. 
