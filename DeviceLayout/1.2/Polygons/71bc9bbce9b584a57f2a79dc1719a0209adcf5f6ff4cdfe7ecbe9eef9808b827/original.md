```
sweep_poly(poly::Polygon, displacement::Point)
```

Return a `Polygon` corresponding to the boundary formed by `poly` swept by `displacement`.

This is the result you would get by painting with a brush shaped like `poly` and moving it along a line by `displacement`.
