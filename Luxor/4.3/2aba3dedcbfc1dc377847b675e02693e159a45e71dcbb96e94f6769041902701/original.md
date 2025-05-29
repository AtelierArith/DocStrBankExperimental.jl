```
polysortbydistance(p, starting::Point)
```

Sort a polygon by finding the nearest point to the starting point, then the nearest point to that, and so on.

You can end up with convex (self-intersecting) polygons, unfortunately.
