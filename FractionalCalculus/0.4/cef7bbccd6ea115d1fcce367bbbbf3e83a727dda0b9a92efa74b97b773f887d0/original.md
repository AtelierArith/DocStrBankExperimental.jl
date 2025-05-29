# Caputo sense Diethelm computation

```
fracdiff(f, α, end_point, h, CaputoDiethelm())
```

Using quadrature weights(derived from product trapezoidal rule) to approximate the derivative.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.007, CaputoDiethelm())
1.128378318687192
```

!!! info "Scope"
    0 < α < 1


Diethelm's method for computingn Caputo sense fractional derivative using [product trapezoidal rule](https://en.wikipedia.org/wiki/Trapezoidal_rule) and [Richardsin extrapolation](https://en.wikipedia.org/wiki/Richardson_extrapolation)

```tex
@article{10.1093/imanum/17.3.479,
author = {DIETTELM, KAI},
title = "{Generalized compound quadrature formulae for finite-part integrals}",
journal = {IMA Journal of Numerical Analysis},
doi = {10.1093/imanum/17.3.479},
}
```
