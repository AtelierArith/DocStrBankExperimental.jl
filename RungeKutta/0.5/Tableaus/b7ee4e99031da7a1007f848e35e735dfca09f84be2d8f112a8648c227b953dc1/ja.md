Lobatto IIIE テーブルの s ステージ

```julia
TableauLobattoIIIE(::Type{T}, s)
TableauLobattoIIIE(s) = TableauLobattoIIIE(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素型 `T` を受け取ります。

参考文献:

```
R.P.K. Chan.
On symmetric Runge-Kutta methods of high order.
Computing, Volume 45, Pages 301-309, 1990.
doi: 10.1007/BF02238798

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```
