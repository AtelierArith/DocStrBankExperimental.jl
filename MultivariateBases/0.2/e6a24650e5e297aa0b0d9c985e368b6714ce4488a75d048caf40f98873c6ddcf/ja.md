```
struct LaguerreBasis{P} <: AbstractMultipleOrthogonalBasis{P}
    polynomials::Vector{P}
end
```

単変数重み関数 $w(x) = \exp(-x)$ に関する直交多項式は、区間 $[0, \infty]$ で定義されます。
