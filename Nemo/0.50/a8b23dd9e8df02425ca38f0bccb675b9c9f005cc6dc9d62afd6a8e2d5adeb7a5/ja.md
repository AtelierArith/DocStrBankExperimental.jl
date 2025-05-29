```
reduce_mod(A::MatElem{T}, B::MatElem{T}) where T <: FieldElem -> MatElem
```

縮約行基本行列 $B$ に対して、$A$ を $B$ で剰余計算します。すなわち、すべてのピボット列はその後ゼロになります。
