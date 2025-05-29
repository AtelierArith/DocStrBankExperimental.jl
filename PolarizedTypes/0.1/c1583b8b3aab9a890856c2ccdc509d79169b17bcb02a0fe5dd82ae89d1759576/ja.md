```
CoherencyMatrix(e11, e21, e12, e22, basis::PolBasis)
```

テンソル積基底 `basis` に対して、成分 e11 e12 e21 e22 を持つコヒーレンシーマトリックスを構築します。`|basis><basis|` で与えられます。

例えば

```julia
c = Coherency(1.0, 0.0, 0.0, 1.0, CirBasis())
```

要素は RR* RL* LR* LL* に対応します。
