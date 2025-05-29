```
colorview(C, gray1, gray2, ...) -> imgC
```

Combine numeric/grayscale images `gray1`, `gray2`, etc., into the separate color channels of an array `imgC` with element type `C<:Colorant`.

As a convenience, the constant `zeroarray` fills in an array of matched size with all zeros.

# Example

```julia
imgC = colorview(RGB, r, zeroarray, b)
```

creates an image with `r` in the red chanel, `b` in the blue channel, and nothing in the green channel.

See also: [`StackedView`](@ref).
