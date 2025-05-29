```julia
est_doa(
    manifold,
    reduction_function;
    init_az,
    init_el,
    kwargs...
)

```

Calculate the Direction Of Arrival (DOA) with respect to the manifold `manifold`. The calculated DOA is returned as `Spherical` object, where the azimuth is counted counter-clockwise from the x axis and the elevation is counted from the xy-plane towards the zenith. If the initial azimuth `init_az` and elevation `init_el` are provided, this will use the hill climbing algorithm. The hill climbing algorithm should be a lot faster than plain maximum search, but may only find a local maximum, which might be desired.

# Examples

Using the signal subspace:

```julia-repl
julia> est_doa(manifold, a -> norm(signal_subspace' * a) / norm(a))
```

Using the noise subspace (MUSIC):

```julia-repl
julia> est_doa(manifold, a -> norm(a) / norm(noise_subspace' * a))
```

# Arguments:

  * `manifold::AbstractManifold`: Manifold of the antenna array
  * `reduction_function`: Function that reduces the manifold vector to a scalar
