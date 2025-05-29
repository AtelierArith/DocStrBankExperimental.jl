```julia
function nonDiagonality(C::Union{Matrix, Diagonal, SorH})
```

$$
C
$$

の対角性からの逸脱の測定値で、$n⋅n$の正方行列として定義されます（Congedo et al., 2008）[🎓](@ref)。

$$
\frac{\sum_{i≠j}|c_{ij}|^2}{(n-1)\sum_{i}|c_{ii}|^2}
$$

$$
C
$$

が対角行列である場合は$0$に等しく、$C$が完全に均一である場合は$1$に等しいです。

**例:**

```julia
using Diagonalizations
C=ones(10, 10)                   # 均一行列
nd=nonDiagonality(C)             # 1である必要があります
D=Diagonal(abs.(randn(10, 10)))  # 対角行列
nd=nonDiagonality(D)             # 0である必要があります
```
