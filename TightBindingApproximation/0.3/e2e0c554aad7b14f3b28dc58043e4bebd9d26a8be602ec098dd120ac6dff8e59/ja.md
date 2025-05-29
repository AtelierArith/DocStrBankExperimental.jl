```
SimpleTBA{
    K<:TBAKind,
    L<:Union{AbstractLattice, Nothing},
    H<:Union{Formula, OperatorSet{<:Quadratic}, Generator{<:OperatorSet{<:Quadratic}}},
    C<:Union{AbstractMatrix, Nothing}
} <:TBA{K, H, C}
```

量子格子系のための単純なタイトバインディング近似。
