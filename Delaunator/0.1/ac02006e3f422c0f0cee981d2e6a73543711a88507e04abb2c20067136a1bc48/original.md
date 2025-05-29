```
PointsFromMatrix(A [,i1=1,i2=2])
```

This implicitly extracts 2d point tuples from a matrix using row indices i1 and i2 for the coordinates. The columns of the matrix because individual points. 

```
PointsFromMatrix(A) == vec(reinterpret(Tuple{Int,Int},A[1:2,:]))
```

This function can be used to transparently map a matrix into a Delaunator set of points. (There is no copying involved).

## Example

```
A = reshape(1:20, 4, 5)
rval = triangulate(PointsFromMatrix(A))) # uses A[1:2,:]
```
