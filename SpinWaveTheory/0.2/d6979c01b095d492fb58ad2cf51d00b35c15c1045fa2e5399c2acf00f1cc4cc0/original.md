```
LSWT{
    K<:TBAKind{:BdG},
    L<:AbstractLattice,
    S<:OperatorGenerator,
    HP<:HolsteinPrimakoff,
    H₀<:CategorizedGenerator,
    H₂<:CategorizedGenerator,
    H<:CategorizedGenerator{<:OperatorSum{<:Quadratic}},
    C<:AbstractMatrix
} <: TBA{K, H, C}
```

Linear spin wave theory for magnetically ordered quantum lattice systems.
