# Extended help

```
intersection(P1::VPolygon, P2::VPolygon; apply_convex_hull::Bool=true)
```

### Output

A `VPolygon`, or an `EmptySet` if the intersection is empty.

### Algorithm

This function applies the [Sutherland–Hodgman polygon clipping algorithm](https://en.wikipedia.org/wiki/Sutherland%E2%80%93Hodgman_algorithm). The implementation is based on the one found in [rosetta code](http://www.rosettacode.org/wiki/Sutherland-Hodgman_polygon_clipping#Julia).
