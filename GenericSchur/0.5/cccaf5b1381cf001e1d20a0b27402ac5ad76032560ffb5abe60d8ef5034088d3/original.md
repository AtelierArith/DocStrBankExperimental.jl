```
balance!(A; scale=true, permute=true) => Abal, B::Balancer
```

Balance a square matrix so that various operations are more stable.

If `permute`, then row and column permutations are found such that `Abal` has the block form `[T₁ X Y; 0 C Z; 0 0 T₂]` where `T₁` and `T₂` are upper-triangular. If `scale`, then a diagonal similarity transform using powers of 2 is found such that the 1-norm of the `C` block (or the whole of `Abal`, if not permuting) is near unity. The transformations are encoded into `B` so that they can be inverted for eigenvectors, etc. Balancing typically improves the accuracy of eigen-analysis.
