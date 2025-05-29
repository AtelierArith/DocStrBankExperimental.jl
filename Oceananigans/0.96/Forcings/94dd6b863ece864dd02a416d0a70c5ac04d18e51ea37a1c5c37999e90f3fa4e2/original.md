```
GaussianMask{D}(center, width)
```

Callable object that returns a Gaussian masking function centered on `center`, with `width`, and varying along direction `D`, i.e.,

```
exp(-(D - center)^2 / (2 * width^2))
```

# Example

Create a Gaussian mask centered on `z=0` with width `1` meter.

```julia
julia> mask = GaussianMask{:z}(center=0, width=1)
```
