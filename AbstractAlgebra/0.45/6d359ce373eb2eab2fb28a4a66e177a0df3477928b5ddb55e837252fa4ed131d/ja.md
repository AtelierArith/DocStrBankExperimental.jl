```
is_invertible_with_inverse(A::MatrixElem{T}; side::Symbol = :left) where {T <: RingElement}
```

リング上の $n \times m$ 行列 $A$ に対して、タプル `(flag, B)` を返します。`side` が `:right` で `flag` が `true` の場合、$B$ は $A$ の右逆行列であり、すなわち $A B$ は $n \times n$ 単位行列です。`side` が `:left` で `flag` が `true` の場合、$B$ は $A$ の左逆行列であり、すなわち $B A$ は $m \times m$ 単位行列です。`flag` が `false` の場合、右逆行列または左逆行列は存在しません。

すべての逆行列の空間を得るためには、$B$ と $C$ が両方とも右逆行列である場合、$A (B - C) = 0$ となり、左逆行列についても同様です。したがって、1つの逆行列から [`kernel`](@ref) を適切に利用することで、すべての逆行列を見つけることができます。
