```julia
update_cache!(cache, H, p, t)

```

Update the internal cache `cache` according to the value of the Hamiltonian `H`  at given time `t`: $cache = -iH(p, t)$. The third argument, `p`  is reserved for passing additional info to the `AbstractHamiltonian` object.  Currently, it is only used by `AdiabaticFrameHamiltonian` to pass the total  evolution time `tf`. To keep the interface consistent across all  `AbstractHamiltonian` types, the `update_cache!` method for all subtypes of  `AbstractHamiltonian` should keep the argument `p`.

Fallback to `cache .= -1.0im * H(p, t)` for generic `AbstractHamiltonian` type.
