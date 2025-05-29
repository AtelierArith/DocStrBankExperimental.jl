```
gmtbegin(name::String=""; fmt)
```

Start a GMT session in modern mode (GMT >= 6). 'name' contains the figure name with or without extension. If an extension is used  (e.g. "map.pdf") it is used to select the image format.

As an alternative use 'fmt' as a string or symbol containing the format (ps, pdf, png, PNG, tif, jpg, eps).

By default name="GMTplot" and fmt="ps"
