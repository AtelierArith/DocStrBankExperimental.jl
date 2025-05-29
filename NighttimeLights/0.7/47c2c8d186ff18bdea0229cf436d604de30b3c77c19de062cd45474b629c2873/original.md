Pixels with no economic activity may show some light due to background noise. These pixels could be in forests, oceans, deserts etc. The `bgnoise_PSTT2021` function generates a background moise mask such that those pixels which are considered dark are marked as 0 and those considered lit are marked as 1. The function uses the datacubes of radiance and ncfobs to generate annual image of the last year the data. The function considers all the pixels below a provided threshold as dark and remaining to be lit. 

```julia
bgnoise_PSTT2021(radiance_datacube, ncfobs_datacube)
```
