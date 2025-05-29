```
polysplit(p, p1, p2)
```

Split a polygon into two where it intersects with a line. It returns two polygons:

```julia
(poly1, poly2)
```

This doesn't always work, of course. For example, a polygon the shape of the letter "E" might end up being divided into more than two parts.
