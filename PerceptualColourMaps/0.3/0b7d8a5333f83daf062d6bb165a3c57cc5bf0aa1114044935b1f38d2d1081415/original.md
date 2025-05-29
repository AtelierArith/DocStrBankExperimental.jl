linearrgbmap: Linear rgb colourmap from black to a specified colour

```
Usage: cmap = linearrgbmap(C, N)

Arguments:  C - 3-vector specifying RGB colour
            N - Number of colourmap elements, defaults to 256

Returns: cmap - N element ColorTypes.RGBA colourmap ranging from [0 0 0]
                to RGB colour C
```

It is suggested that you pass the resulting colour map to equalisecolourmap() to obtain a map with uniform steps in perceptual lightness

```
> cmap = equalisecolourmap("rgb", linearrgbmap(C, N))
```

See also: equalisecolourmap, ternarymaps
