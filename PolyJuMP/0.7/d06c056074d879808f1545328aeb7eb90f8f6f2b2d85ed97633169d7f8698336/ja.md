```
struct Poly{PB<:AbstractPolynomialBasis} <: AbstractPoly
    polynomial_basis::PB
end
```

多項式変数 $v^\top p$ ここで、$v$ は新しい決定変数のベクトルであり、$p$ は基底 `polynomial_basis` の多項式のベクトルです。
