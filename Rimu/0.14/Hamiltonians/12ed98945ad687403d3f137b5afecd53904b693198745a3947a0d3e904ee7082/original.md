```
HubbardRealSpace(address; geometry=PeriodicBoundaries(M,), t=ones(C), u=ones(C, C), v=zeros(C, D))
```

Hubbard model in real space. Supports single or multi-component Fock state addresses (with `C` components) and various (rectangular) lattice geometries in `D` dimensions.

$$
  \hat{H} = -\sum_{\langle i,j\rangle,σ} t_σ a^†_{iσ} a_{jσ} +
  \frac{1}{2}\sum_{i,σ} u_{σσ} n_{iσ} (n_{iσ} - 1) +
  \sum_{i,σ≠τ}u_{στ} n_{iσ} n_{iτ}
$$

If `v` is nonzero then this calculates $\hat{H} + \hat{V}$ by adding the harmonic trapping potential

$$
    \hat{V} = \sum_{i,σ,d} v_{σd} x_{di}^2 n_{iσ}
$$

where $x_{di}$ is the distance of site $i$ from the centre of the trap along dimension $d$.

## Address types

  * [`BoseFS`](@ref): Single-component Bose-Hubbard model.
  * [`FermiFS`](@ref): Single-component Fermi-Hubbard model.
  * [`CompositeFS`](@ref): For multi-component models.

Note that a single component of fermions cannot interact with itself. A warning is produced if `address`is incompatible with the interaction parameters `u`.

## Geometries

Implemented [`CubicGrid`](@ref)s for keyword `geometry`

  * [`PeriodicBoundaries`](@ref)
  * [`HardwallBoundaries`](@ref)
  * [`LadderBoundaries`](@ref)

Default is `geometry=PeriodicBoundaries(M,)`, i.e. a one-dimensional lattice with the number of sites `M` inferred from the number of modes in `address`.

## Other parameters

  * `t`: the hopping strengths. Must be a vector of length `C`. The `i`-th element of the vector corresponds to the hopping strength of the `i`-th component.
  * `u`: the on-site interaction parameters. Must be a symmetric matrix. `u[i, j]` corresponds to the interaction between the `i`-th and `j`-th component. `u[i, i]` corresponds to the interaction of a component with itself. Note that `u[i,i]` must be zero for fermionic components.
  * `v`: the trap potential strengths. Must be a matrix of size `C × D`. `v[i,j]` is the strength of the trap for component `i` in the `j`th dimension.
