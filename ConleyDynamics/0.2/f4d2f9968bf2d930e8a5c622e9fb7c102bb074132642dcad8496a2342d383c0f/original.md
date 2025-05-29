```
remove_exit_set(lc::LefschetzComplex, mvf::CellSubsets)
```

Exit set removal for a multivector field on a Lefschetz subcomplex.

It is assumed that the Lefschetz complex `lc` is a topological manifold and that `mvf` contains a multivector field that is created via either `create_planar_mvf` or `create_spatial_mvf`. The function identifies cells on the boundary at which the flows exits the region covered by the Lefschetz complex. If this exit set is closed, we have found an  isolated invariant set and the function returns a Lefschetz complex `lcr` restricted to it, as well as the restricted multivector field `mvfr`. If the exit set is not closed, a warning is displayed and the function returns the restricted Lefschetz complex and multivector field obtained by removing the closure of the exit set. In the latter case, unexpected results might be obtained.
