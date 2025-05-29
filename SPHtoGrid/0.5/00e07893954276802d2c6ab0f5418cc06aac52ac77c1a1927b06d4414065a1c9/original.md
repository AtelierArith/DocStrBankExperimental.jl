```
write_fits_image(filename::String, image::Array{<:Real};
                units::String = "[i.u.]",
                snap::Integer = 0)
```

Writes a mapped allsky image to a FITS file and stored units and snapshot number in the header.
