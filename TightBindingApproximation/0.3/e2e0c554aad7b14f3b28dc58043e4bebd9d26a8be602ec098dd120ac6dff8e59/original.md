```
SimpleTBA{
    K<:TBAKind,
    L<:Union{AbstractLattice, Nothing},
    H<:Union{Formula, OperatorSet{<:Quadratic}, Generator{<:OperatorSet{<:Quadratic}}},
    C<:Union{AbstractMatrix, Nothing}
} <:TBA{K, H, C}
```

Simple tight-binding approximation for quantum lattice systems.
