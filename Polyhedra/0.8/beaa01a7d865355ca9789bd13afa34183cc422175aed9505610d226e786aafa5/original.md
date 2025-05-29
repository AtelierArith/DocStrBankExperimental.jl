```
vrep(points::PointIt; d::FullDim)
```

Creates a V-representation for the polytope of full dimension `d` equal to the convex hull of the points `points`.

### Examples

The convex hull of $(0, 0)$, $(0, 1)$ and $(1/2, 1/2)$ can be created as follows using exact arithmetic

```julia
vrep([[0, 0], [0, 1], [1//2, 1//2]])
```

or as follows using floating point arithmetic

```julia
vrep([[0, 0], [0, 1], [1/2, 1/2]])
```
