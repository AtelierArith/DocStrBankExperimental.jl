equalisecolourmap - Equalise colour contrast over a colourmap equalizecolormap

```
Usage: newrgbmap = equalisecolourmap(rgblab, map, formula, W, sigma, diagnostics)
                   equalizecolormap(....

Arguments:     rgblab - String "RGB" or "LAB" indicating the type of data
                        in map.
                  map - A Nx3 RGB or CIELAB colour map
                        or an array of ColorTypes.RGB{Float64} values
              formula - String "CIE76" or "CIEDE2000"
                    W - A 3-vector of weights to be applied to the
                        lightness, chroma and hue components of the
                        difference equation. It is recommended that you
                        use [1, 0, 0] to only take into account lightness.
                        If desired used  [1, 1, 1] for the full formula.
                sigma - Optional Gaussian smoothing parameter.
               cyclic - Boolean flag indicating whether the colour map is
                        cyclic. This affects how smoothing is applied at
                        the end points.
          diagnostics - Optional boolean flag indicating whether diagnostic
                        plots should be displayed.  Defaults to false.

Returns:    newrgbmap - RGB colour map adjusted so that the perceptual
                        contrast of colours along the colour map is constant.
                        This is a Nx3 Array of Float64 values.

For full documentation see equalisecolourmap()
                                 ^     ^
```

See also: cmap, sineramp, circlesineramp
