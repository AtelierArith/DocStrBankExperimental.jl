```
productstatemps(physdims::Dims, Dmax=1; state=:Vacuum, mpsorthog=:Right)
```

Return an MPS representing a product state with local Hilbert space dimensions given by `physdims`.

By default all bond-dimensions will be 1 since the state is a product state. However, to embed the product state in a manifold of greater bond-dimension, `Dmax` can be set accordingly.

The indvidual states of the MPS sites can be provided by setting `state` to a list of column vectors. Setting `state=:Vacuum` will produce an MPS in the vacuum state (where the state of each site is represented by a column vector with a 1 in the first row and zeros elsewhere). Setting `state=:FullOccupy` will produce an MPS in which each site is fully occupied (ie. a column vector with a 1 in the last row and zeros elsewhere).

The argument `mpsorthog` can be used to set the gauge of the resulting MPS.

# Example

```julia-repl
julia> ψ = unitcol(1,2); d = 6; N = 30; α = 0.1; Δ = 0.0; ω0 = 0.2; s = 1

julia> cpars = chaincoeffs_ohmic(N, α, s)

julia> H = spinbosonmpo(ω0, Δ, d, N, cpars)

julia> A = productstatemps(physdims(H), state=[ψ, fill(unitcol(1,d), N)...]) # MPS representation of |ψ>|Vacuum>
```
