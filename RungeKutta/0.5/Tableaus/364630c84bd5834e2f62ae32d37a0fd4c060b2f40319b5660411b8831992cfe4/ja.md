Lobatto IIIB テーブルの s ステージ

```julia
TableauLobattoIIIB(::Type{T}, s)
TableauLobattoIIIB(s) = TableauLobattoIIIB(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素型 `T` を受け取ります。

参考文献:

```
Byron Leonard Ehle.
On Padé approximations to the exponential function and a-stable methods for the numerical solution of initial value problems.
Research Report CSRR 2010, Dept. AACS, University of Waterloo, 1969.

Laurent O. Jay.
Lobatto Methods.
In: Engquist B. (eds). Encyclopedia of Applied and Computational Mathematics. Springer, Berlin, Heidelberg. 2015.
doi: 10.1007/978-3-540-70529-1_123.
```
