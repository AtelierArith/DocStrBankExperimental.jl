```
struct LaguerreBasis{P} <: AbstractMultipleOrthogonalBasis{P}
    polynomials::Vector{P}
end
```

単変数重み関数 $w(x) = \exp(-x)$ に関して、区間 $[0, \infty]$ での直交多項式。
