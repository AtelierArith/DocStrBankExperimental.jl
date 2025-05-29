```
Moore-Penrose predictor / corrector
```

Moore-Penrose continuation algorithm.

Additional information is available on the [website](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/MooreSpence/).

# Constructors

`alg = MoorePenrose()`

`alg = MoorePenrose(tangent = PALC())`

# Fields

  * `tangent::Any`: Tangent predictor, for example `PALC()`
  * `method::BifurcationKit.MoorePenroseLS`: Moore Penrose linear solver. Can be BifurcationKit.direct, BifurcationKit.pInv or BifurcationKit.iterative
  * `ls::BifurcationKit.AbstractLinearSolver`: (Bordered) linear solver
