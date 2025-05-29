```
print_irreducible_bz_paths(cryst::Crystal)
```

Prints certain high-symmetry points with suggested paths between them. The points lie in the irreducible Brillouin, which is reduced from the first Brillouin zone by the point group symmetries of the crystal. Coordinates are printed in reciprocal lattice units (RLU), i.e., as multiples of the conventional lattice vectors of `cryst`. These high-symmetry paths were originally formulated in Ref. [1] and implemented in [SeeK-path](https://github.com/giovannipizzi/seekpath). Sunny obtains this functionality from the [Brillouin.jl](https://github.com/thchr/Brillouin.jl) package.

See also [`view_bz`](@ref) for an interactive visualization of these high-symmetry paths.

## References

1. [Y. Hinuma, G. Pizzi, Y. Kumagai, F. Oba, I. Tanaka, *Band structure diagram paths based on crystallography*, Comp. Mat. Sci. **128**, 140 (2017)](https://doi.org/10.1016/j.commatsci.2016.10.015).
