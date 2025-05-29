```
mean_hue(h1::Real, h2::Real)
mean_hue(a::C, b::C) where {C <: Colorant}
```

Compute the mean of two hue angles in degrees.

If the inputs are HSV-like or Lab-like color objects, this will also return a hue, not a color. If one of the colors is achromatic, i.e. has zero saturation or chroma, the hue of the other color is returned instead of the mean.

When the hue difference is exactly 180 degrees, which of the two mean hues is returned depends on the implementation. In other words, it may vary by the color type and version.
