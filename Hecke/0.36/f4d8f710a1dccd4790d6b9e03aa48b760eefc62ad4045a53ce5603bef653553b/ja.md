```
change_coefficient_ring(R::Ring, L::ModAlgAssLat{ZZRing}) -> ModAlgAss
```

与えられた格子 $L$ が $\mathbf{Z}$-順序 $L$ の上にあるとき、環 $R$ の上の $L \otimes R$ を返します。

モジュールは代数なしで定義され、作用は $\rank(O)$ 個の生成子によって与えられます。
