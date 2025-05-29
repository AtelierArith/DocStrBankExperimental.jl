```
restrict_dynamics(lc::LefschetzComplex, mvf::CellSubsets, lcsub::Cells)
```

Restrict a multivector field to a Lefschetz subcomplex.

For a given multivector field `mvf` on a Lefschetz complex `lc`, and a subcomplex which is given by the locally closed set represented by `lcsub`, create the associated Lefschetz subcomplex `lcreduced` and the induced multivector field `mvfreduced` on the subcomplex. The multivectors of the new multivector field are the intersections of the original multivectors and the subcomplex.
