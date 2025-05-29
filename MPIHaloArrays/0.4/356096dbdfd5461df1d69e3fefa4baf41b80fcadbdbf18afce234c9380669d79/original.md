```
global_domain_indices(A::MPIHaloArray)
```

Get the array indices of the domain region of `A` (i.e. excluding halo regions) in the global frame of reference. The order of the returned indices is (ilo, ihi, jlo, jhi, ...).

# Returns

  * `NTuple{Int, 2 * NDimensions}` : A tuple of both lo and hi indices for each dimension
