```
anti_uniformizer(P::NumFieldOrderIdeal) -> NumFieldElem
```

与えられた素イデアル $P$ に対して、$P$ を含む数体の要素 $a$ を返します。ここで、valuation(a, P) == -1、valuation(a, Q) = 0 は $P$ の素共役において、他のすべての素イデアルに対して非負の評価を持ちます。
