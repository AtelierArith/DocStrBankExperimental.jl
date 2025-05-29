```
pix_write_implied_format(
    filename::AbstractString,     # The name of the file to write to.
    pix::Pix;                     # The image to write.
    quality::Integer  = Int32(75), # If the image is JPEG the quality to encode as.
    progressive::Bool = false     # If the image is JEPG use progressive encoding?
)::Bool
```

Write the image to a file based on the file extension.  The quality and progressive parameters are only used if the image type is JPEG.  Returns true on success or false on failure.
