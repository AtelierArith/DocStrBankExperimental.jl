```
reduce_mod!(A::MatElem{T}, B::MatElem{T}) where T <: FieldElem
```

縮約行基本行列 $B$ に対して、$A$ の行を $B$ に対して剰余を取るように縮約します。すなわち、すべてのピボット列はその後ゼロになります。
