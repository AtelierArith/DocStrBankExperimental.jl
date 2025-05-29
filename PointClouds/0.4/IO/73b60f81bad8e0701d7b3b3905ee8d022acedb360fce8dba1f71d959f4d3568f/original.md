```
color_channels(Integer, p::PointRecord)
color_channels(Integer, points, inds = :)
```

Obtain the “raw” intensity associated with each color channel as a tuple of unsigned 16-bit integers. For PDRFs 2, 3, 5, and 7, this returns three values that correspond to the red, green, and blue channel whereas PDRFs 8 and 10 include a fourth value for the near infrared channel. Values should be normalized to cover the range 0 to 65535. For PDRFs that do not include color information `missing` is returned.

See also: [`PointRecord`](@ref), [`intensity`](@ref)
