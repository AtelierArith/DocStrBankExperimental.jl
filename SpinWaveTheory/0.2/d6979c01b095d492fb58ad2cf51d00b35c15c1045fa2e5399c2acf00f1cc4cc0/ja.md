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

磁気秩序量子格子系のための線形スピン波理論。
