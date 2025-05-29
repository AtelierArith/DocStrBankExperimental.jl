```
FroehlichPolaron(address::OccupationNumberFS{M}; kwargs...) <: AbstractHamiltonian
```

The Froehlich polaron Hamiltonian for a 1D lattice with `M` momentum modes is given by

$$
H = (p̂_f - p)^2/m + ωN̂ - v Σₖ(âₖ^† + â₋ₖ)
$$

where $p$ is the total momentum, $p̂_f = Σ_k k âₖ^† âₖ$ is the momentum operator for the bosons, and $k$ part of the momentum lattice with separation $2π/l$. $N̂$ is the number operator for the bosons.

# Keyword Arguments

  * `p=0.0`: the total momentum $p$.
  * `v=1.0`: the coupling strength $v$.
  * `mass=1.0`: the particle mass $m$.
  * `omega=1.0`: the oscillation frequency of the phonons $ω$.
  * `l=1.0`: the box size in real space $l$. Provides scale parameter of the momentum   lattice.
  * `momentum_cutoff=nothing`: the maximum boson momentum allowed for an address.
  * `mode_cutoff`: the maximum number of bosons in each momentum mode. Defaults to the maximum   value supported by the address type [`OccupationNumberFS`](@ref).

# Examples

```jldoctest
julia> fs = OccupationNumberFS(0,0,0)
OccupationNumberFS{3, UInt8}(0, 0, 0)

julia> ham = FroehlichPolaron(fs; v=0.5)
FroehlichPolaron(fs"|0 0 0⟩{8}"; v=0.5, mass=1.0, omega=1.0, l=1.0, p=0.0, mode_cutoff=255)

julia> dimension(ham)
16777216

julia> dimension(FroehlichPolaron(fs; v=0.5, mode_cutoff=5))
216
```

See also [`OccupationNumberFS`](@ref), [`dimension`](@ref), [`AbstractHamiltonian`](@ref).
