```julia
tofockbasis(
    S::Array{GF<:Keldysh.AbstractTimeGF, 1},
    ed::KeldyshED.EDCore
) -> Vector{GF} where GF<:Keldysh.AbstractTimeGF

```

Transform a block-diagonal evolution operator `S` written in the eigenbasis of the system into the Fock state basis.
