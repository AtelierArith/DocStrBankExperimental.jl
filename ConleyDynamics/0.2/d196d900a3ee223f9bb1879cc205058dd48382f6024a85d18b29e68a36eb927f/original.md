```
lefschetz_reduction(lc::LefschetzComplex, redpairs::Vector{Vector{String}})
```

Apply a sequence of elementary reductions to a Lefschetz complex.

The reduction pairs have to be specified in the argument `redpairs`. Each entry has to be a vector of length two which contains an elementary reduction pair in label form. In particular, the dimensions of the two cells in the pair have to differ by one, and once the pair is reached in the reduction sequence, one cell has to be a face of the other. The function returns a new Lefschetz complex, where all cells in `redpairs` have been removed.
