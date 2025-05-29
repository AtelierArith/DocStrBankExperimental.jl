```
struct LegendreBasis{P} <: AbstractGegenbauerBasis{P}
    polynomials::Vector{P}
end
```

区間 $[-1, 1]$ における単変数重み関数 $w(x) = 1$ に関する直交多項式。
