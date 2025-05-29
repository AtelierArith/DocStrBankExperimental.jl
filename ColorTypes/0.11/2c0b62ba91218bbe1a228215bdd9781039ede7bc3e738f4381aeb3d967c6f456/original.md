ColorTypes summary:

Type hierarchy:

```
                          Colorant{T,N}
             Color{T,N}                    TransparentColor{C,T,N}
     AbstractRGB{T}                  AlphaColor{C,T,N}  ColorAlpha{C,T,N}
```

Concrete types:

  * `RGB`, `BGR`, `XRGB`, `RGBX`, `RGB24` are all subtypes of `AbstractRGB`
  * `HSV`, `HSL`, `HSI`, `XYZ`, `xyY`, `Lab`, `LCHab`, `Luv`, `LCHuv`, `DIN99`, `DIN99d`, `DIN99o`, `LMS`, `YIQ`, `YCbCR`, `Oklab`, and `Oklch` are subtypes of `Color{T,3}`
  * Alpha-channel analogs in such as `ARGB` and `RGBA` for most of those types (with a few exceptions like `RGB24`, which has `ARGB32`)
  * Grayscale types `Gray` and `Gray24` (subtypes of `Color{T,1}`), and the corresponding transparent types `AGray`, `GrayA`, and `AGray32`
  * Trait functions `eltype`, `length`, `alphacolor`, `coloralpha`, `color_type`, `base_color_type`, `base_colorant_type`, `ccolor`
  * Getters `red`, `green`, `blue`, `alpha`, `gray`, `comp1`, `comp2`, `comp3`

Use `?` to get more information about specific types or functions.
