```
relative_homology(lc::LefschetzComplex,subc::Cells,subc0::Cells)
```

Compute the relative homology of a Lefschetz complex with respect to a subcomplex. The computation is performed over the field associated with the Lefschetz boundary matrix.

In this implementation, relative homology of the pair `cl(subc), cl(subc0))` is computed. An error is raised if `cl(subc0)` is not a subset of `cl(subc)`. The homology is returned as a vector `betti` of Betti numbers, where `betti[k]` is the Betti number in dimension `k-1`.
