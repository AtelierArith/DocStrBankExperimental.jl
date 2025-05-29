```
struct ProbabilistsHermiteBasis{P} <: AbstractHermiteBasis{P}
    polynomials::Vector{P}
end
```

単変量重み関数 $w(x) = \exp(-x^2/2)$ に関して、区間 $[-\infty, \infty]$ での直交多項式。
