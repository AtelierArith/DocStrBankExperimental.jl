```
locally_isometric_sublattice(M::HermLat, L::HermLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> HermLat
```

有理的に等長なエルミート格子 `M` と `L` が $E/K$ 上にあり、$\mathcal O_K$ の素イデアル `p` が与えられたとき、$N_q = M_q$ で $q \neq p$ のとき、$N_p$ が $L_p$ と等長であるような `M` の部分格子 `N` を返します。
