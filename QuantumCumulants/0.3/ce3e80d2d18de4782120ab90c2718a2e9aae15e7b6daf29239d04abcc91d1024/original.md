```
Pauli <: QSym
```

Pauli operator on a [`PauliSpace`](@ref) representing the Pauli operators σx, σy and σz for two-level spin systems.  The field axis represents x, y and z as 1, 2 and 3, repectively. The used rewriting rule is σj⋅σk → δjk + i⋅ϵjkl⋅σl.

# Examples

```
julia> h = PauliSpace("Spin-1/2")
ℋ(Spin-1/2)

julia> σx = Pauli(h,:σ,1)
σx
```
