```
localfilter!(dst, A, B, filter!; order=FORWARD_FILTER) -> dst
```

overwrites `dst` with the result of filtering the source `A` by the kernel specified by `B`, with ordering `order`, and the function `filter!` which is called as:

```
filter!(dst, A, order, ker, i, J)
```

for every index `i` of `dst` and with `J` the subset of indices in the local neighborhood of `i` and:

```
ker = kernel(Dims{ndims(A)}, B)
```

the array representing the filter kernel. The function `filter!` shall compute the result of the local filtering operation and store it in the destination `dst` at position `i`.

  * If `order = FORWARD_FILTER`, then `J` is the subset of all indices `j` such that `A[j]` and `B[j-i]` are in-bounds. This is the natural ordering to implement discrete correlations.
  * If `order = REVERSE_FILTER`, then `J` is the subset of all indices `j` such that `A[j]` and `B[i-j]` are in-bounds. This is the natural ordering to implement discrete convolutions.

To be agnostic to the ordering, just use `B[order(i,j)]` in the code of `filter!` to automatically yield either `B[j-i]` or `B[i-j]` depending on whether `order` is `FORWARD_FILTER` or `REVERSE_FILTER`.
