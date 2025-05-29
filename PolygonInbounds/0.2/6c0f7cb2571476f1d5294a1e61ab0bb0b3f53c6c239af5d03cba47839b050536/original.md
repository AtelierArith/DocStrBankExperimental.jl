```
s = inpoly2(vert, node, [edge=Nothing, atol=0.0, rtol=eps(), outformat=InOnOut{1,0,-1}])
```

Check all points defined by `vert` are inside, outside or on bounds of polygon defined by `node` and `edge`.

`vert` and `node` are matrices with the x-coordinates in the first and the y-coordinates in the second column.

`edge` is an integer matrix of same size as `node`. The first column contains the index of the starting node, the second column the index of the ending node. The polygon needs to be closed. It may contain unconnected cycles.

A point is considered on boundary, if its Euclidian distance to any edge is less than or equal `max(atol, rtol * span)`, where span is the maximum extension of the polygon in either direction.

If a point is considered on bounds, no further check is made to determine it it is inside or  outside numerically.

Expected effort of the algorithm is `(N+M)*log(M)`, where `M` is the number of points and `N` is the number of polygon edges.
