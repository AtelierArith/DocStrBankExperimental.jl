# Caputo sense fractional derivative high order approximation.

!!! info
    By using `CaputoHighOrder` method, we can set $0<\alpha<2$


### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.01, 2, CaputoHighOrder())
1.1283791670955123
```

```tex
@article{Li2017HighOrderAT,
  title={High-Order Approximation to Caputo Derivatives and Caputo-type Advection–Diffusion Equations: Revisited},
  author={Changpin Li and Minhao Cai},
  journal={Numerical Functional Analysis and Optimization},
  year={2017},
  volume={38},
  pages={861 - 890}
}
```
