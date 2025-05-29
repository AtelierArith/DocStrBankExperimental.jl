Lobatto IIIC タブローと s ステージ

```julia
TableauLobattoIIIC(::Type{T}, s)
TableauLobattoIIIC(s) = TableauLobattoIIIC(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

参考文献:

```
F. H. Chipman.
A-stable Runge-Kutta processes.
BIT, Volume 11, Pages 384-388, 1971.
doi: 10.1007/BF01939406.

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```
