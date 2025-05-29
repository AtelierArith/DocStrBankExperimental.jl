```
pix2ang{T, O <: Order}(map::HealpixMap{T, O}, ipix) -> (Float64, Float64)
pix2ang{T, O <: Order}(map::PolarizedHealpixMap{T, O}, ipix) -> (Float64, Float64)
```

Return the pair (`theta`, `phi`), where `theta` is the colatitude and `phi` the longitude of the direction of the pixel center with index `ipix`.
