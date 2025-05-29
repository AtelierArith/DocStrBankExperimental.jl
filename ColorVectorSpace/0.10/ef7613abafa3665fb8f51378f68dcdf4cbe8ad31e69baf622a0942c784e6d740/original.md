```
RGBRGB(rr, gr, br, rg, gg, bg, rb, gb, bb)
```

Represent the [tensor product](https://en.wikipedia.org/wiki/Tensor_product) of two RGB values.

# Example

```jldoctest julia> a, b = RGB(0.2f0, 0.3f0, 0.5f0), RGB(0.77f0, 0.11f0, 0.22f0) (RGB{Float32}(0.2f0,0.3f0,0.5f0), RGB{Float32}(0.77f0,0.11f0,0.22f0))

julia> a ⊗ b RGBRGB{Float32}:  0.154  0.022  0.044  0.231  0.033  0.066  0.385  0.055  0.11
