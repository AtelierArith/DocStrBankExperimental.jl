```
write_fits_image(filename::String, image::Array{<:Real}, 
                        par::mappingParameters; 
                        units::String="[i.u.]",
                        snap::Integer=0)
```

Writes a mapped image to a FITS file and stored the essential mapping parameters in the header.
