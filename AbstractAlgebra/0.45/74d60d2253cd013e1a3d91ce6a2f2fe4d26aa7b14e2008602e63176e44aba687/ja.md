```
isequal(a::ResFieldElem{T}, b::ResFieldElem{T}) where {T <: RingElement}
```

$ a == b $ が正確に等しい場合は `true` を返し、それ以外の場合は `false` を返します。この関数は、残差のデータが不正確な場合、例えば冪級数の場合に便利です。この関数によって等しいと宣言されるのは、冪級数が正確に同じで、同じ精度である場合のみです。
