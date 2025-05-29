```
GutzwillerSampling(::AbstractHamiltonian; g)
```

Wrapper over any [`AbstractHamiltonian`](@ref) that implements Gutzwiller sampling. In this importance sampling scheme the Hamiltonian is modified as follows

$$
\tilde{H}_{ij} = H_{ij} e^{-g(H_{ii} - H_{jj})} .
$$

This way off-diagonal spawns to higher-energy configurations are discouraged and spawns to lower-energy configurations encouraged for positive `g`.

# Constructor

  * `GutzwillerSampling(::AbstractHamiltonian, g)`
  * `GutzwillerSampling(::AbstractHamiltonian; g)`

After construction, we can access the underlying Hamiltonian with `G.hamiltonian` and the `g` parameter with `G.g`.

# Example

```jldoctest
julia> H = HubbardMom1D(BoseFS(1,1,1); u=6.0, t=1.0)
HubbardMom1D(fs"|1 1 1⟩"; u=6.0, t=1.0)

julia> G = GutzwillerSampling(H, g=0.3)
GutzwillerSampling(HubbardMom1D(fs"|1 1 1⟩"; u=6.0, t=1.0); g=0.3)

julia> get_offdiagonal(H, BoseFS(2, 1, 0), 1)
(BoseFS{3,3}(1, 0, 2), 2.0)

julia> get_offdiagonal(G, BoseFS(2, 1, 0), 1)
(BoseFS{3,3}(1, 0, 2), 0.8131393194811987)
```

# Observables

To calculate observables, pass the transformed Hamiltonian `G` to [`AllOverlaps`](@ref) with keyword argument `transform=G`.
