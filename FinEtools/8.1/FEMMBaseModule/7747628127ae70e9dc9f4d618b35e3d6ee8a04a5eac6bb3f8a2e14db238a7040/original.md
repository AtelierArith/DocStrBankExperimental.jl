```
associategeometry!(self::AbstractFEMM, geom::NodalField{GFT}) where {GFT}
```

Associate geometry field with the FEMM.

There may be operations that could benefit from pre-computations that involve a geometry field. If so, associating the geometry field gives the FEMM a chance to save on repeated computations.

Geometry field is normally passed into any routine that evaluates some forms (integrals) over the mesh.  Whenever the geometry passed into a routine is not consistent with the one for which `associategeometry!()` was called before, `associategeometry!()` needs to be called with the new geometry field.
