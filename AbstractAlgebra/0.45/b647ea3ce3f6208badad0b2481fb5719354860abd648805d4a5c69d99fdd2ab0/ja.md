```
isequal(x::NCPolyRingElem{T}, y::NCPolyRingElem{T}) where T <: NCRingElem
```

$ x == y $ が正確に等しい場合は `true` を返し、それ以外の場合は `false` を返します。この関数は、係数が不正確な多項式、例えば冪級数の場合に便利です。冪級数が正確に同じで、同じ精度である場合にのみ、この関数によって等しいと見なされます。
