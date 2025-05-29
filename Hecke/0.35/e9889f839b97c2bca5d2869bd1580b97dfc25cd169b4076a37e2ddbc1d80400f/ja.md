```
maximal_integral_lattice(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbstractLat
```

与えられた格子 `L` と、`L` の固定環 $\mathcal O_K$ の素イデアル `p` があり、$L_p$ のノルムが整数である場合、`L` の周囲空間において `p` で最大整数であり、`p` とは異なるすべての場所で `L` と局所的に一致する格子 `M` を返します。
