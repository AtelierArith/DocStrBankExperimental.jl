`lnullspace(m::AbstractMatrix)`

The left nullspace of `m`, that is a matrix whose rows form a basis of the space of vectors `v` such that `iszero(permutedims(v)*m)`.
