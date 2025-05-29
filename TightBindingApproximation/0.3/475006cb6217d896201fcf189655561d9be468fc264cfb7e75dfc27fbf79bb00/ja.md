```
CompositeTBA{
    K<:TBAKind,
    L<:Union{AbstractLattice, Nothing},
    S<:Union{OperatorSet{<:Operator}, Generator{<:OperatorSet{<:Operator}}},
    Q<:Quadraticization,
    H<:Union{OperatorSet{<:Quadratic}, Generator{<:OperatorSet{<:Quadratic}}},
    C<:Union{AbstractMatrix, Nothing}
} <:TBA{K, H, C}
```

量子格子系のための複合タイトバインディング近似。
