```
support(F::Vector{<:MP.AbstractPolynomialLike}, vars=MP.variables(F), T::Type{<:Integer}=Int32)
```

多項式系統 `F` のサポートを、指定された変数 `vars` で計算します。返される行列の要素型は `T` です。
