```
fine_mixed_cells(f::Vector{<:MP.AbstractPolynomialLike}; show_progress=true, max_tries = 10)
fine_mixed_cells(support::Vector{<:Matrix}; show_progress=true, max_tries = 10)
```

Compute all (fine) mixed cells of the given `support` induced by a generic lifting. This guarantees that all induced initial forms are binomials. If the chosen lifting is not generic, then the algorithm is restarted. This happens at most `max_tries` times many. Returns a `Vector` of all mixed cells and the corresponding lifting or `nothing` if the algorithm wasn't able to compute fine mixed cells. This can happen due to some current technical limitations.
