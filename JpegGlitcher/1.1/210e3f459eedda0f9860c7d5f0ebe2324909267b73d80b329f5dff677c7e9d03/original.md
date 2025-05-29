```
glitch(img::AbstractMatrix; rng::AbstractRNG=default_rng(), nflips::Integer=10, quality::Integer=100)
```

`glitch` will turn an image into a compressed JPEG format with JPEGTurbo.jl and randomly change some bytes (safe to change) of the encoded image.

## Keyword arguments

  * `rng::AbstractRNG`: the random number generator used to select and modify bytes.
  * `n::Integer`: the number of bytes to modify.
  * `quality::Integer`: the encoding quality of the JPEG (lower gives worse quality).
