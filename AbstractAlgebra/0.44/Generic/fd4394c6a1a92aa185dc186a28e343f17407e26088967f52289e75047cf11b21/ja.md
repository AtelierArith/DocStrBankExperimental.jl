```
minpoly(S::Ring, M::MatRingElem{T}) where {T <: RingElement}
```

行列 $M$ の最小多項式 $p$ を返します。結果の多項式の多項式環 $S$ を指定する必要があり、行列は正方行列でなければなりません。
