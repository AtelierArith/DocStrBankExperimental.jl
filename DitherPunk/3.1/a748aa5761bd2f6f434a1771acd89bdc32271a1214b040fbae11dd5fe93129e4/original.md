```
OrderedDither(mat::AbstractMatrix)
```

Generalized ordered dithering algorithm using a threshold map. Takes a normalized threshold matrix `mat`.

When applying the algorithm to an image, the threshold matrix is repeatedly tiled to match the size of the image. It is then applied as a per-pixel threshold map. Optionally, this final threshold map can be inverted by selecting `invert_map=true`.
