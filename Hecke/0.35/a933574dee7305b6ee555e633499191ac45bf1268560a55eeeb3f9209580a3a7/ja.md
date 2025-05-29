```
trred_matrix(A::Vector{ <: AssociativeAlgebraElem}) -> MatElem
```

行列 $M$ を返します。ここで $M_{ij} = \mathrm{tr}(A_i \cdot A_j)$ であり、$\mathrm{tr}$ は縮約トレースです。
