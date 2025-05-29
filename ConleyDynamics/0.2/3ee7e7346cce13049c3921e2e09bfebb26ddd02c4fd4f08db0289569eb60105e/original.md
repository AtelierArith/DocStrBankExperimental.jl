```
homology(lc::LefschetzComplex)
```

Compute the homology of a Lefschetz complex.

The homology is returned as a vector `betti` of Betti numbers, where `betti[k]` is the Betti number in dimension `k-1`. The computations are performed over the field associated with the Lefschetz complex boundary matrix.
