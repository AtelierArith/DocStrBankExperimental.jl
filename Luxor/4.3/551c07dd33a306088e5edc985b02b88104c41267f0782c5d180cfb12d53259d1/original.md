```
setantialias(n)
```

Set the current antialiasing to a value between 0 and 6:

```
antialias_default  = 0, the default antialiasing for the subsystem and target device
antialias_none     = 1, use a bilevel alpha mask
antialias_gray     = 2, use single-color antialiasing (using shades of gray for black text on a white background, for example)
antialias_subpixel = 3, take advantage of the order of subpixel elements on devices such as LCD panels
antialias_fast     = 4, perform some antialiasing but prefer speed over quality
antialias_good     = 5, balance quality against performance
antialias_best     = 6, render at the highest quality, sacrificing speed if necessary
```

This affects subsequent graphics, but not text, and it doesn't apply to all types of output file.
