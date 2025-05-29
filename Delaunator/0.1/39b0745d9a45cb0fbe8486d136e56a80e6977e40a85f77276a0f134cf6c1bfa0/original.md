```
bt, cdata = update!(points, bt, cdata)
```

Reuse the memory and arrays to update the triangulation. Note that the resulting return values may be new as this routine can allocate new arrays if needed to handle the updated set of points. This implements the key step of the Delaunator method. 
