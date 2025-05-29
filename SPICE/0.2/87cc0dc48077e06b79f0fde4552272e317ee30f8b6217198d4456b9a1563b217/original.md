```
dskmi2(vrtces, plates, finscl, corscl, worksz, voxpsz, voxlsz, makvtl, spaisz)
```

Make spatial index for a DSK type 2 segment.

### Arguments

  * `vrtces`: Vertices
  * `plates`: Plates
  * `finscl`: Fine voxel scale
  * `corscl`: Coarse voxel scale
  * `worksz`: Workspace size
  * `voxpsz`: Voxel-plate pointer array size
  * `voxlsz`: Voxel-plate list array size
  * `makvtl`: Vertex-plate list flag
  * `spxisz`: Spatial index integer component size

### Output

  * `spaixd`: Double precision component of spatial index.
  * `spaixi`: Integer component of spatial index.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dskmi2_c.html)
