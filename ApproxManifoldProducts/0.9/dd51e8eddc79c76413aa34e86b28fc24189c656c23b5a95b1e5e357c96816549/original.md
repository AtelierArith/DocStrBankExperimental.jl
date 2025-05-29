```julia
mmd!(MF, val, a, b; ...)
mmd!(MF, val, a, b, N; ...)
mmd!(MF, val, a, b, N, M; ...)
mmd!(MF, val, a, b, N, M, threads; bw)

```

MMD disparity (i.e. 'distance') measure based on Kernel Hilbert Embeddings between two beliefs.

Notes:

  * This is the in-place version (well more in-place than mmd)

DevNotes:

  * TODO dont assume equally weighted particles
  * TODO profile SIMD vs SLEEF
  * TODO optimize memory
  * TODO make multithreaded

See also: [`mmd`](@ref), [`ker`](@ref)
