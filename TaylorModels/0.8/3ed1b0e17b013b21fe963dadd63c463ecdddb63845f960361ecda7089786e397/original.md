```
integrate(a::TM{T,S}, c0)
integrate(a::TM{TaylorN{T},S}, c0, cc0)
```

Integrates the one-variable Taylor Model (`TaylorModel1` or `RTaylorModel1`) with respect to the independent variable. `c0` is the integration constant; if omitted it is taken as zero. When the coefficients of `a` are `TaylorN` variables, the domain is specified by `cc0::IntervalBox`.

---

```
integrate(fT, which)
```

Integrates a `fT::TaylorModelN` with respect to `which` variable. The returned `TaylorModelN` corresponds to the Taylor Model of the definite integral ∫f(x) - ∫f(expansion_point).
