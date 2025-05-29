```
struct AffineFEStateMap{A,B,C,D,E,F} <: AbstractFEStateMap
```

A structure to enable the forward problem and pullback for affine finite element operators `AffineFEOperator`.

# Parameters

  * `biform::A`: `IntegrandWithMeasure` defining the bilinear form.
  * `liform::B`: `IntegrandWithMeasure` defining the linear form.
  * `spaces::C`: `Tuple` of finite element spaces.
  * `plb_caches::D`: A cache for the pullback operator.
  * `fwd_caches::E`: A cache for the forward problem.
  * `adj_caches::F`: A cache for the adjoint problem.
