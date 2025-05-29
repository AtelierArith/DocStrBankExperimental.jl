```
lu(A::MatrixElem{T}, P = SymmetricGroup(nrows(A))) where {T <: FieldElement}
```

タプル $r, p, L, U$ を返します。ここで、$A$ のランク、$P$ に属する $A$ の置換 $p$、下三角行列 $L$ および上三角行列 $U$ です。ここで、$p(A)$ は $A$ の行の与えられた置換 $p$ からなる行列を表します。
