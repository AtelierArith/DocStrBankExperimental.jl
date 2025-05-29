```
eigenspace(M::MatElem{T}, lambda::T; side::Symbol = :left)
  where T <: FieldElem -> MatElem{T}
```

行列 $M$ の固有値 $\lambda$ に関する固有空間の基底を与える行列を返します。`side` が `:left` の場合は行を、`side` が `:right` の場合は列を返します。`side` が `:right` の場合、右固有空間が計算されます。すなわち、$Mv = \lambda v$ となるベクトル $v$ です。`side` が `:left` の場合、左固有空間が計算されます。すなわち、$vM = \lambda v$ となるベクトル $v$ です。
