```
extract(imfile, n=10, i=10, tolerance=0.01; shrink=n)
```

`extract()` extracts the most common colors from an image from the image file `imfile` by finding `n` dominant colors, using `i` iterations. You can (and probably should) shrink larger images before running this function.

Returns a ColorScheme.
