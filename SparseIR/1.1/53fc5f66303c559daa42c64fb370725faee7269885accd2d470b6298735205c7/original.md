```
AugmentedBasis <: AbstractBasis
```

Augmented basis on the imaginary-time/frequency axis.

Groups a set of additional functions, `augmentations`, with a given `basis`. The augmented functions then form the first basis functions, while the rest is provided by the regular basis, i.e.:

```
u[l](x) == l < naug ? augmentations[l](x) : basis.u[l-naug](x),
```

where `naug = length(augmentations)` is the number of added basis functions through augmentation. Similar expressions hold for Matsubara frequencies.

Augmentation is useful in constructing bases for vertex-like quantities such as self-energies [^wallerberger2021] and when constructing a two-point kernel that serves as a base for multi-point functions [^shinaoka2018].

!!! warning
    Bases augmented with `TauConst` and `TauLinear` tend to be poorly conditioned. Care must be taken while fitting and compactness should be enforced if possible to regularize the problem.

    While vertex bases, i.e. bases augmented with `MatsubaraConst`, stay reasonably well-conditioned, it is still good practice to treat the Hartree–Fock term separately rather than including it in the basis, if possible.


See also: [`MatsubaraConst`](@ref) for vertex basis [^wallerberger2021], [`TauConst`](@ref), [`TauLinear`](@ref) for multi-point [^shinaoka2018]

[^wallerberger2021]: https://doi.org/10.1103/PhysRevResearch.3.033168

[^shinaoka2018]: https://doi.org/10.1103/PhysRevB.97.205111
