```
detect(emitted::Dict{<:XRay,<:Real}, det::EDSDetector, response::Matrix{Float64}; noise=false)
```

Returns a Spectrum as though the intensities in `emitted` were detected on the specified detector. `noise=true` will add Poisson noise to the resulting measured `Spectrum`.
