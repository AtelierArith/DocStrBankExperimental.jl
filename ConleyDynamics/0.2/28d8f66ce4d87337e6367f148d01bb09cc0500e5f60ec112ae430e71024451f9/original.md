```
relative_homology(lc::LefschetzComplex,subc::Cells)
```

Compute the relative homology of a Lefschetz complex with respect to a subcomplex. The computation is performed over the field associated with the Lefschetz boundary matrix.

The subcomplex is the closure of the cells in `subc`, which can be given either as indices or labels. The homology is returned as a vector `betti` of Betti numbers, where `betti[k]` is the Betti number in dimension `k-1`.
