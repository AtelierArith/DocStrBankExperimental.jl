```
blockDiagonalize(P::Partition, verbose = true; epsilon = 1e-8, complex = false)
```

Determines a block-diagonalization of a (Jordan)-algebra given by a partition `P` using a randomized algorithm. `blockDiagonalize(P)` returns a real block-diagonalization `blkd`, if it exists, otherwise `nothing`.

`blockDiagonalize(P; complex = true)` returns the same, but with complex valued matrices, and should be used if no real block-diagonalization was found. To use the complex matrices practically, remember that a Hermitian matrix `A` is positive semidefinite iff `[real(A) -imag(A); imag(A) real(A)]` is positive semidefinite.

## Output

  * `blkd.blkSizes` is an integer array of the sizes of the blocks.
  * `blkd.blks` is an array of length `dim(P)` containing arrays of (real/complex) matrices of sizes `blkd.blkSizes`. I.e. `blkd.blks[i]` is the image of the basis element `P.matrix .== i`.
