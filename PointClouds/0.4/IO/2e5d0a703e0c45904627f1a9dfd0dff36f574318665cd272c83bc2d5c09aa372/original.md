```
color_channels(p::PointRecord)
color_channels(points, inds = :)
```

Obtain the intensity associated with each color channel as a tuple of values normalized to the range from 0 to 1. For PDRFs 2, 3, 5, and 7, this returns three values that correspond to the red, green, and blue channel whereas PDRFs 8 and 10 include a fourth value for the near infrared channel. For PDRFs that do not include color information `missing` is returned.

See also: [`PointRecord`](@ref), [`intensity`](@ref)
