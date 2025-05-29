```
fillshapes(uc, shapes...[; sites, scale, kw...])
```

Create a lattice sample with geometry defined by the given shapes. The lattice is filled with sites that are inside the shapes.

## Arguments

  * `uc`: The `UnitCell` of the lattice. Might also be a lattice type.
  * `shapes`: The shapes to fill the lattice with.

## Keyword Arguments

  * `sites`: If given, an attepmt will be made to fill the lattice with the given number of sites.   The scaling will be approximate and relying on assumptions that the shapes do not overlap.
  * `scale`: The scaling factor for the shapes. If `sites` is given, the scaling factor will be   calculated automatically.

All other keyword arguments are passed to the lattice constructor. See [`span_unitcells`](@ref) for more information.
