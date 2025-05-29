function find*symmetric*tensor_size(N, dim)

```
Nの各次元におけるdim次元の対称テンソルの要素数を返します。
結果はbinomial(N-1+dim, dim)で与えられます。

例:
julia> find_symmetric_tensor_size(20, 6)
177100
```
