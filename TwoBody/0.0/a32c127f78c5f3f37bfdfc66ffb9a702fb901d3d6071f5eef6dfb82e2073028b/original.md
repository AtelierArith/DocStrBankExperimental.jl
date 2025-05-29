`FiniteDifferenceMethod(Δr=0.1, rₘₐₓ=50.0, R=Δr:Δr:rₘₐₓ, l=0, direction=:c, solver=:LinearAlgebra)`

| Arguments           | Default          | Description                                                                                                                                      |
|:------------------- |:---------------- |:------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Δr::Real`          | `0.1`            | Radial grid spacing. A uniform grid spacing is used, $r_{i+1} = r_{i} + \Delta r$.                                                               |
| `rₘₐₓ::Real`        | `50.0`           | The maximum value of the radial grid. This value is not directly used in the calculation, but it is used to determine the `R`.                   |
| `R::StepRangeLen`   | `Δr:Δr:rₘₐₓ`     | Radial grid. The origin must be excluded from the grid to avoid divergence of the Coulomb potential and the centrifugal potential at the origin. |
| `l::Int`            | `0`              | Angular momentum quantum number. This is a positive integer, $0 \leq l$.                                                                         |
| `direction::Symbol` | `:c`             | The direction of the finite difference, `:c` for central, :f for forward, `:b` for backward.                                                     |
| `solver::Symbol`    | `:LinearAlgebra` | The solver for eigenvalue problem, `:LinearAlgebra` or `:ArnoldiMethod`.                                                                         |
