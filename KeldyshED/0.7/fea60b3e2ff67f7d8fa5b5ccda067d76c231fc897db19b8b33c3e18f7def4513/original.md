```julia
tofockbasis(
    M::Array{Array{T<:Number, 2}, 1},
    ed::KeldyshED.EDCore
) -> Vector

```

Transform a block-diagonal matrix written in the eigenbasis into the Fock state basis.

## Arguments

  * `M`:  List of matrices' diagonal blocks.
  * `ed`: An Exact Diagonalization object defining the invariant subspace structure and       partial eigenbases within the subspaces.
