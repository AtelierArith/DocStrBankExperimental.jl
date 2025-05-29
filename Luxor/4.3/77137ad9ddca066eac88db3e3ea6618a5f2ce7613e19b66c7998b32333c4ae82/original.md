```
pathsample(path::Path, spacing;
    steps=10)
```

Return a new Path that resamples the `path` such that each line and curve of the original path is divided into sections that are approximately `spacing` units long.

The `steps` parameter is used when approximating the length of any curve (Bezier) sections. For measurement purposes, each Bezier curve is divided in `steps` straight lines; the error will be smaller for flatter curves and larger for more curvy ones.
