```
MultiChannelColor(i₁, i₂, ...)
MultiChannelColor((i₁, i₂, ...))
MultiChannelColor{T}(...)                # coerce to element type T
```

Represent multichannel "raw" colors, which lack `convert` methods to standard color spaces. If `c` is a `MultiChannelColor` object, then `Tuple(c)` is a tuple of intensities (one per channel).

[`ColorMixture`](@ref) is an alternative with a built-in conversion to RGB.
