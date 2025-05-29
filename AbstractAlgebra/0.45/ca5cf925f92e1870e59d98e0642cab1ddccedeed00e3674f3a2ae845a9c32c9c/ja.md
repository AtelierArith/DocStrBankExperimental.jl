```
is_nilpotent(A::MatrixElem{T}) where {T <: RingElement}
```

行列 `A` がニルポテントであるかどうかを返します。すなわち、自然数 $k$ が存在して $A^k = 0$ である場合です。`A` が正方行列でない場合は例外が発生します。
