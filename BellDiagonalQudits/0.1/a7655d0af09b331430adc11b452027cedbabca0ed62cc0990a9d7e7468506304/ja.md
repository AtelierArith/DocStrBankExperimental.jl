```
uniform_bell_sampler(n, d, object=:magicSimplex, precision=10)
```

`n` 個の一様に分布した $d^2$ ベル対角状態の配列を作成し、`precision` 桁に丸められた `CoordState` として表現します。

`object=:enclosurePolytope` を使用して、すべての $coords \leq 1/d$ を持つエンクロージャーポリトープ内の CoordStates を作成します。
