```
CoherencyMatrix(e11, e21, e12, e22, basis::NTuple{2, PolBasis})
```

テンソル積基底 `|basis[1]><basis[2]|` に対して、成分 e11 e12 e21 e22 を持つコヒーレンシーマトリックスを構築します。注意してください、basis[1] と basis[2] は異なる可能性があります。

例えば

```julia
c = Coherency(1.0, 0.0, 0.0, 1.0, CirBasis(), LinBasis())
```

要素は RX* RY* LX* LY* に対応します。
