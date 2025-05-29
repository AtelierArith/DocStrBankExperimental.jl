```
isequal(x::MatrixElem{T}, y::MatrixElem{T}) where {T <: NCRingElement}
```

$ x == y $ が正確に等しい場合は `true` を返し、それ以外の場合は `false` を返します。この関数は、行列の要素が不正確な場合、例えば冪級数の場合に便利です。冪級数が同じ精度で正確に同じである場合にのみ、この関数によって等しいと見なされます。
