```
dense_matrix_type(::Type{T}) where T<:NCRingElement
dense_matrix_type(::T) where T<:NCRingElement
dense_matrix_type(::Type{S}) where S<:NCRing
dense_matrix_type(::S) where S<:NCRing
```

型 `T` の係数を持つ行列の型を返します。それぞれ `elem_type(S)`。

環インターフェースの実装は、引数が `NCRingElement` のサブタイプであるメソッドを提供する必要があるだけで、他のバリアントはそのメソッドを呼び出すことで実装されます。
