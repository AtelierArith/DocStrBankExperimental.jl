```
is_invertible(A::MatrixElem{T}) where {T <: RingElement}
```

与えられた正方行列が可逆であればtrueを返し、そうでなければfalseを返します。逆行列も計算する必要がある場合は、`is_invertible_with_inverse`を使用してください。
