```
remesh!(self::ImageMesher, edge_length_ratio = 1.0)
```

Perform a re-meshing step.

If  no mesh exists,  the initial mesh is created; otherwise a coarsening sequence of coarsen surface -> smooth -> coarsen volume -> smooth is performed. The current element size (`self.currentelementsize`) is used. So don't forget to update the current elements size for the next iteration of the re-meshing algorithm.

  * `edge_length_ratio` = the largest allowed ratio of the lengths of the longest and the shortest edge length in the tetrahedron to be produced by coarsening (default 1.0). If this is supplied as greater than 1.0, for instance 2.0, extra long spikey tetrahedra are prevented.

After meshing the vertices, tetrahedra, and material identifiers,  can be retrieved as `self.v`, `self.t`, and `self.tmid`.
