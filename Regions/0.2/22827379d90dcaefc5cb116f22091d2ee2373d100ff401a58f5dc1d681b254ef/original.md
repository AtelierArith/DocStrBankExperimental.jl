```
invert(x::Region)
-(x::Region)
```

Invert a region. Inversion mirrors a region at the origin. A region is inverted by inverting each of its runs. Since the runs of a region are sorted by their row and column coordinates, the order of the runs is inversed as well.
