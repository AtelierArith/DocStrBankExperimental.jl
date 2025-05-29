`centre_of_mass` finds the mean of coordinates weighted by nighttime lights radiance_datacube. 

```julia
spaster = sparse(Array(radiance_image)[:,:,1])
centre_of_mass(spaster, dims(radiance_image))
```
