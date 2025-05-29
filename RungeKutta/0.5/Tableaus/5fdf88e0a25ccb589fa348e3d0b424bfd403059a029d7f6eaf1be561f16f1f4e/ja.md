Lobatto III タブロー s ステージ

```julia
TableauLobattoIII(::Type{T}, s)
TableauLobattoIII(s) = TableauLobattoIII(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

このタブローは、Lobatto IIIC* とも呼ばれることがあります。

参考文献:

```
John C. Butcher.
Integration processes based on Radau quadrature formulas
Mathematics of Computation, Volume 18, Pages 233-244, 1964.
doi: 10.1090/S0025-5718-1964-0165693-1.

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```
