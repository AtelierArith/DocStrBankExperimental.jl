```
pairwise_hamming(X, Y; step=1, step_left, step_right, as_vec=true, kwargs...)
pairwise_hamming(X; as_vec, step, kwargs...)
```

Return all hamming distances between sequences of `X` and `Y`. In the second form, consider pairs of sequences in `X`.

Only consider sequences every `step`. `step_left` and `step_right` can be used to skip sequence either in `X` or in `Y`. This is useful for large alignment, as the number of computations grows with the product     of the size of the alignments

By default, the return value is a vector organized like `[H(1,2), H(1,3), ..., H(M-1, M)]` with `H` standing for hamming distance and `M` for the number of sequences. If a matrix is prefered, use `as_vec=false`

Extra keyword arguments are passed to `hamming`.
