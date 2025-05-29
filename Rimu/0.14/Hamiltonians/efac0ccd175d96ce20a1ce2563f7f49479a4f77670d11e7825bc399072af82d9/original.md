```
GuidingVectorSampling
```

Wrapper over any [`AbstractHamiltonian`](@ref) that implements guided vector a.k.a. guided wave function sampling. In this importance sampling scheme the Hamiltonian is modified as follows.

$$
\tilde{H}_{ij} = v_i H_{ij} v_j^{-1}
$$

and where `v` is the guiding vector. `v_i` and `v_j` are also thresholded to avoid dividing by zero (see below).

# Constructors

  * `GuidingVectorSampling(::AbstractHamiltonian, vector, eps)`
  * `GuidingVectorSampling(::AbstractHamiltonian; vector, eps)`

`eps` is a thresholding parameter used to avoid dividing by zero; all values below `eps` are set to `eps`. It is recommended that `eps` is in the same value range as the guiding vector. The default value is set to `eps=norm(v, Inf) * 1e-2`

After construction, we can access the underlying hamiltonian with `G.hamiltonian`, the `eps` parameter with `G.eps`, and the guiding vector with `G.vector`.

# Example

```jldoctest
julia> H = HubbardReal1D(BoseFS(1,1,1); u=6.0, t=1.0);

julia> v = DVec(starting_address(H) => 10; capacity=1);

julia> G = GuidingVectorSampling(H, v, 0.1);

julia> get_offdiagonal(H, starting_address(H), 4)
(BoseFS{3,3}(2, 0, 1), -1.4142135623730951)

julia> get_offdiagonal(G, starting_address(G), 4)
(BoseFS{3,3}(2, 0, 1), -0.014142135623730952)
```

# Observables

To calculate observables, pass the transformed Hamiltonian `G` to [`AllOverlaps`](@ref) with keyword argument `transform=G`.
