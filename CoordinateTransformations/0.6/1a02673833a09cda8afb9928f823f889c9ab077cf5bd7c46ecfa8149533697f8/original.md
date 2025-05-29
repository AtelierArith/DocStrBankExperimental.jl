```
AffineMap(from_points => to_points) → trans
```

Create an Affine transformation that approximately maps the `from` points to the `to` points. At least `n+1` non-degenerate points are required to map an `n`-dimensional space. If there are more points than this, the transformation will be over-determined and a least-squares solution will be computed.
