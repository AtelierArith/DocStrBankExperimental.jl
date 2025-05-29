```
polysortbyangle(pointlist::Vector{Point}, refpoint=minimum(pointlist))
```

Sort the points of a polygon into order. Points are sorted according to the angle they make with a specified point.

The `refpoint` can be chosen, but the default minimum point is usually OK too:

```
polysortbyangle(parray, polycentroid(parray))
```
