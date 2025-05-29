```
decompose(S::LazySet, block_options; [block_size]::Int=1)
```

Decompose a high-dimensional set into a Cartesian product of overapproximations of the projections over uniformly-sized subspaces.

### Input

  * `S`             – set
  * `block_options` – overapproximation option or mapping from block indices to a                    corresponding overapproximation option
  * `block_size`    – (optional; default: `1`) size of the blocks

### Output

A `CartesianProductArray` containing the low-dimensional approximated projections.
