```
dskb02(handle, dladsc)
```

Return bookkeeping data from a DSK type 2 segment.

### Arguments

  * `handle`: DSK file handle
  * `dladsc`: DLA descriptor

### Output

  * `nv`: Number of vertices in model
  * `np`: Number of plates in model
  * `nvxtot`: Number of voxels in fine grid
  * `vtxbds`: Vertex bounds
  * `voxsiz`: Fine voxel edge length
  * `voxori`: Fine voxel grid origin
  * `vgrext`: Fine voxel grid exent
  * `cgscal`: Coarse voxel grid scale
  * `vtxnpl`: Size of vertex-plate correspondence list
  * `voxnpt`: Size of voxel-plate pointer list
  * `voxnpl`: Size of voxel-plate correspondence list

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskb02_c.html)
