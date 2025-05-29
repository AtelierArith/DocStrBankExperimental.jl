```
build_basis(
    ham, address=starting_address(ham);
    cutoff, filter, sizelim, sort=false, kwargs...
) -> basis
build_basis(ham, addresses::AbstractVector; kwargs...)
```

Get all basis element of a linear operator `ham` that are reachable (via non-zero matrix elements) from the address `address`, returned as a vector. Instead of a single address, a vector of `addresses` can be passed. Does not return the matrix, for that purpose use [`BasisSetRepresentation`](@ref).

Providing an energy cutoff will skip addresses with diagonal elements greater than `cutoff`. Alternatively, an arbitrary `filter` function can be used instead. Addresses passed as arguments are not filtered.

Providing a `max_depth` will limit the size of the basis by only visiting addresses that are connected to the `starting_address` through `max_depth` hops through the Hamiltonian. Similarly, providing `minimum_size` will stop the bulding process after the basis reaches a length of at least `minimum_size`.

A maximum basis size `sizelim` can be set which will throw an error if the expected dimension of `ham` is larger than `sizelim`. This may be useful when memory may be a concern. These options are disabled by default.

!!! warning
    ```
    The order the basis is returned in is arbitrary and non-deterministic. Use
    `sort=true` if the ordering matters.
    ```

