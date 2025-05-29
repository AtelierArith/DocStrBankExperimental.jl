```
state_supersinglet([T=ComplexF64,] N::Integer = 3; v::Real = 1)
```

は、可視性 `v` を持つ `N` 部分の `N` レベルのシングレット状態を生成します。この状態は、すべての当事者に対する同時回転に対して不変です: $(U ⊗ ... ⊗ U) ρ (U ⊗ ... ⊗ U)' = ρ$。

参考文献: Adán Cabello, [arXiv:quant-ph/0203119](https://arxiv.org/abs/quant-ph/0203119)
