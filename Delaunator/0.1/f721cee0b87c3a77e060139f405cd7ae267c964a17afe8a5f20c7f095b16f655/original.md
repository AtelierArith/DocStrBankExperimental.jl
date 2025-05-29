```
dualcell(t, i)
dualcell(t, centers, i)
```

Return the finite or infinite polygon description of the dual cell to a given point index in the triangulation. The dual cell is the  Voronoi cell to a Delaunay triangulation. 

The default usage uses the circumcenters of the Delaunay triangles  as the coordinates of the Voroni vertices. However,  you can override this by giving another collection of centers.  The number of centers must be equal to the number  of triangles. 
