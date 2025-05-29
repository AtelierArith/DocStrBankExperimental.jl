```
ids = inwhichpolygon(point::Matrix{Real}, D::Vector{GMTdataset}; on_is_in=false, pack=false)
```

or

```
ids = inwhichpolygon(x, y, D::Vector{GMTdataset}; on_is_in=false, pack=false)
```

Finds the IDs of the polygons enclosing the query points in `point`. Each row in the matrix `point` contains the coordinates of a query point. Query points that don't fall in any polygon get an ID = 0. Returns either an $Int$ or a $Vector{Int}$ depending on the number of input query points.

  * `D`: A Vector of GMTdadaset defining the polygons.
  * `point`: A Mx2 matrix or a two elements vector with the x and y point coordinates.
  * `x, y`:  Specifies the x-coordinates and y-coordinates of 2-D query points as separate vectors (or two scalars).
  * `on_is_in`: If `on_is_in=true` then points exactly on the border are considered inside. Default is `false`.
  * `pack`: If `pack=true` then a vector of vectors is returned with the IDs of the hit polygons and the indices of the query points that hit each polygon. That is: ids[1] contains indices of `D` that recieved at least a hit; ids[2] contains the indices of the query `point` that hit the polygon D[ids[1]], etc.

### Example:

```
pts = [[1 2 3;1 2 3;1 2 3][:] [1 1 1;2 2 2; 3 3 3][:]];
D = triplot(pts, noplot=true);
points = [2.4 1.2; 1.4 1.4];
ids = inwhichpolygon(points, D);
# Plot the triangulation and the query points.
plot(D)
plot!(D[ids[1]], fill=:grey)
plot!(D[ids[2]], fill=:green)
plot!(points, marker=:star, ms="12p", fill=:blue, show=true)
```
