# Riemann Liouville sense derivative using Triangular Strip Matrix to discrete and compute.

```
fracdiff(f, α, end_point, h, RLDiffMatrix())
```

Using [Triangular Strip Matrix](https://en.wikipedia.org/wiki/Triangle_strip) to approximate fractional derivative.

### Example

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.0001, RLInt_Matrix())
```

!!! info
    Triangular Strip Matrix method returns the derivative in the interval $[0, T]$ in `Vector`


```tex
@article{2009,
title={Matrix approach to discrete fractional calculus II: Partial fractional differential equations},
DOI={10.1016/j.jcp.2009.01.014},
author={Podlubny, Igor and Chechkin, Aleksei and Skovranek, Tomas and Chen, YangQuan and Vinagre Jara, Blas M.},
}
```
