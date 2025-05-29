```
extract_weighted_colors(imfile, n=10, i=10, tolerance=0.01; shrink = 2)
```

Extract colors and weights of the clusters of colors in an image file. Returns a ColorScheme and weights.

Example:

```
pal, wts = extract_weighted_colors(imfile, n, i, tolerance; shrink = 2)
```
