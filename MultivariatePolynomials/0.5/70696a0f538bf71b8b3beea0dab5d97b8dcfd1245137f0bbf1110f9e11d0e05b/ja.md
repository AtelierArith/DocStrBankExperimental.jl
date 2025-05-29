```
multiplication_preserves_monomial_order(P::Type{<:AbstractPolynomialLike})
```

モノミアルの型 `monomial_type(P)` の乗算において順序が保持されるかどうかを示す `Bool` を返します。つまり、もし `a < b` であれば、任意のモノミアル `c` に対して `a * c < b * c` となります。デフォルトでは `true` を返します。これは [`Polynomial`](@ref) によって使用されるため、乗算がモノミアルの順序を保持しないモノミアル型でも、この関数のメソッドを実装して `false` を返すことで [`Polynomial`](@ref) と一緒に使用することができます。
