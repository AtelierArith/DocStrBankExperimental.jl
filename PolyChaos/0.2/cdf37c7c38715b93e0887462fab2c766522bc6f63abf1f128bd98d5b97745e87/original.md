```
rm_compute(weight::Function,lb::Real,ub::Real,Npoly::Int=4,Nquad::Int=10;quadrature::Function=clenshaw_curtis)
```

Given a positive `weight` function with domain `(lb,ub)`, i.e. a function $w: [lb, ub ] \rightarrow \mathbb{R}_{\geq 0}$, this function creates `Npoly` recursion coefficients `(α,β)`.

The keyword `quadrature` specifies what quadrature rule is being used.
