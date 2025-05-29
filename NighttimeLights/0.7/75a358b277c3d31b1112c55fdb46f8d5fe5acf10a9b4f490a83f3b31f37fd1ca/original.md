```julia
using Plots
res = 15
R1 = 2
R2 = 5
lat = 19.07
long = 72.87
bounds, mask = annular_ring(radiance_image, R1, R2, lat, long, res) 
plot(Rasters.mask(radiance_image[bounds...], with = mask))
```
