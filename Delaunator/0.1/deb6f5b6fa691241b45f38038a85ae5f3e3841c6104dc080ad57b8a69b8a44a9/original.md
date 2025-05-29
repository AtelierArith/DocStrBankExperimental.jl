```
hullpoly(t)
```

Return the coordinates of the convex hull suitable for plotting as a polygon. 

# Example

```
t = triangulate(rand(StableRNG(1), Point2f, 10))
f = scatter(t.points)
poly!(f.axis,collect(hullpoly(t)),color=:transparent, strokewidth=1)
f
```
