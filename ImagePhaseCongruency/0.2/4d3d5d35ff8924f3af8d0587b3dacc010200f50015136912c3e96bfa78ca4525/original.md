Create $1/f^p$ spectrum noise images.

When displayed as a surface these images also generate great landscape terrain.

```
Usage: img = noiseonf(sze, p)

Arguments:
    sze::Tuple{Integer, Integer} or ::Integer
              - A tuple (rows, cols) or single value specifying size of
                image to produce.
      p::Real - Exponent of spectrum decay = 1/(f^p)

Returns:
   img::Array{Float64,2} - The noise image with specified spectrum.


Reference values for p:
            p = 0   - raw Gaussian noise image.
              = 1   - gives the supposedly 1/f 'standard' drop-off for
                      'natural' images.
              = 1.5 - seems to give the most interesting 'cloud patterns'.
              = > 2 - produces 'blobby' images.
```
