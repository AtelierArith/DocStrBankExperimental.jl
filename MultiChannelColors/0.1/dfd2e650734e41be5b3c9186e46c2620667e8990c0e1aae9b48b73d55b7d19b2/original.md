```
ColorMixture((rgb₁, rgb₂, ...), (i₁, i₂, ...))
ColorMixture((rgb₁, rgb₂, ...), i₁, i₂, ...)
ColorMixture{T}(...)                       # coerce intensities to element type
```

Represent a multichannel color with a defined conversion to RGB. `rgbⱼ` is an RGB color corresponding to channel `j`, and its intensity is `iⱼ`. Colors are converted to RGB, `convert(RGB, c)`, using intensity-weighting: `rgb = sum(ivalues .* rgbvalues)`.

[`MultiChannelColor`](@ref) is an alternative that does not require an `rgb` list and has no built-in conversion to RGB.
