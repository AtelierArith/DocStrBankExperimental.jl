```
struct AbstractGegenbauerBasis{P} <: AbstractMultipleOrthogonalBasis{P}
    polynomials::Vector{P}
end
```

単変数重み関数 $w(x) = (1 - x^2)^{\alpha - 1/2}$ に関して、区間 $[-1, 1]$ での直交多項式。
