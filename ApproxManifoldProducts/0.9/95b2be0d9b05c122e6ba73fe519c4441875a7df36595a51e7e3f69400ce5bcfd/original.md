```julia
mmd(MF, a, b; ...)
mmd(MF, a, b, N; ...)
mmd(MF, a, b, N, M; ...)
mmd(MF, a, b, N, M, threads; bw)

```

MMD disparity (i.e. 'distance') measure based on Kernel Hilbert Embeddings between two beliefs.

Notes:

  * This is a wrapper to the in-place `mmd!` function.

Related

mmd!, ker
