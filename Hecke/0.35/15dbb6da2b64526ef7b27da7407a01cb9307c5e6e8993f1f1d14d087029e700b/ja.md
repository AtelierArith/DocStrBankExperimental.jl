```
factor(A::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}
```

$$
A
$$

の素イデアル因数分解を辞書として計算します。キーは素イデアルの約数です：もし`lp = factor_dict(A)`であれば、`keys(lp)`は$A$の素イデアルの約数であり、`lp[P]`は`keys(lp)`のすべての$P$に対する$P$-進評価です。
