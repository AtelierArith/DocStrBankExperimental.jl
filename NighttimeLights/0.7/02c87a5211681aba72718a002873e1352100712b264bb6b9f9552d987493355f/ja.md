```julia
using Plots
res = 15
R = 2
lat = 19.07
long = 72.87
bounds, mask = annular_ring(radiance_image, R, lat, long, res) 
plot(Rasters.mask(radiance_image[bounds...], with = mask))
```
