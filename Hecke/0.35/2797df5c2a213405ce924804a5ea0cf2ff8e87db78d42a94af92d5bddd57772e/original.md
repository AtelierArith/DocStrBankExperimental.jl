```
genus_representatives(L::HermLat; max = inf, use_auto = true,
                                             use_mass = false)
                                                      -> Vector{HermLat}
```

Return representatives for the isometry classes in the genus of the hermitian lattice `L`. At most `max` representatives are returned.

If `L` is definite, the use of the automorphism group of `L` is enabled by default. It can be disabled by `use_auto = false`. In the case where `L` is indefinite, the entry `use_auto` has no effect. The computation of the mass can be enabled by `use_mass = true`.
