```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

ネットワーク内の相互作用を*1回*スワップします。第二引数として`PermutationConstraint`が指定されていない場合、すべての種の次数分布は維持されます。
