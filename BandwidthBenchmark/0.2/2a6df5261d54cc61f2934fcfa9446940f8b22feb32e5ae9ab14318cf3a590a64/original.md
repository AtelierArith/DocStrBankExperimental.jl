Measure the memory bandwidth using the following streaming kernels with corresponding data access pattern (Notation: S - store, L - load, WA - write allocate). All variables are vectors, `s` is a scalar:

```
init (S1, WA): Initilize an array: `a = s`. Store only.
sum (L1): Vector reduction: `s += a`. Load only.
copy (L1, S1, WA): Classic memcopy: `a = b`.
update (L1, S1): Update vector: `a = a * scalar`. Also load + store but without write allocate.
triad (L2, S1, WA): Stream triad: `a = b + c * scalar`.
daxpy (L2, S1): Daxpy: `a = a + b * scalar`.
striad (L3, S1, WA): Schoenauer triad: `a = b + c * d`.
sdaxpy (L3, S1): Schoenauer triad without write allocate: `a = a + b * c`.
```

Keyword arguments:

  * `N` (default: `120_000_000`): length of vectors
  * `nthreads` (default: `Threads.nthreads()`): number of Julia threads to use
  * `niter` (default: `10`): # of times we repeat the measurement
  * `alignment` (default: `64`): array alignment
  * `verbose` (default: `false`): print result table + thread information etc.
  * `write_allocate` (default: `false`): include write allocate compensation factors
