```
rsvd(A, n, p=0)
```

Compute partial singular value decomposition of `A` using a randomized algorithm.

# Arguments

`A`: input matrix.

`n::Int`: number of singular value/vector pairs to find.

`p::Int=0`: number of extra vectors to include in computation.

# Output

`::SVD`: singular value decomposition.

!!! warning "Accuracy"
    This variant of the randomized singular value decomposition is the most commonly found implementation but is not recommended for accurate computations, as it often has trouble finding the `n` largest singular pairs, but rather finds `n` large singular pairs which may not necessarily be the largest.


# Implementation note

This function calls `rrange`, which uses naive randomized rangefinding to compute a basis for a subspace of dimension `n` (Algorithm 4.1 of [^Halko2011]), followed by `svd_restricted()`, which computes the exact SVD factorization on the restriction of `A` to this randomly selected subspace (Algorithm 5.1 of [^Halko2011]).

Alternatively, you can mix and match your own randomized algorithm using any of the randomized range finding algorithms to find a suitable subspace and feeding the result to one of the routines that computes the `SVD` restricted to that subspace.
