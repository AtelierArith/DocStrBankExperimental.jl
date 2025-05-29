```
struct ChebyshevBasisSecondKind{P} <: AbstractChebyshevBasis{P}
    polynomials::Vector{P}
end
```

単変数重み関数 $w(x) = \sqrt{1 - x^2}$ に関して、区間 $[-1, 1]$ で直交多項式。
