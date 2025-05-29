```
MSC(h)
MSC(h, l; linear=false)
```

Calculate the most saturated color in sRGB gamut for any given hue `h` by finding the corresponding corner in LCHuv space. Optionally, the lightness `l` may also be specified.

# Arguments

  * `h`: Hue [0,360] in LCHuv space
  * `l`: Lightness [0,100] in LCHuv space

# Keyword arguments

  * `linear` : If true, the saturation is linearly interpolated between black/ white and `MSC(h)` as the gamut is approximately triangular in L-C section.

!!! note
    `MSC(h)` returns an `LCHuv` color, but `MSC(h, l)` returns a saturation value. This behavior might change in a future release.

