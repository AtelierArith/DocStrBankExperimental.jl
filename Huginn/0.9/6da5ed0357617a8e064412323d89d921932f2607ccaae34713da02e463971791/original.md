```
halfar_solution(R, t, h₀, r₀, A, n, physical_parameters::PhysicalParameters)
```

Return the evaluation of the Halfar solution for the SIA equation.

Arguments:

  * `R`: Radial distance. The solution has polar symmetry around the center of origin.
  * `t`: Time.
  * `h₀` and `r₀`: Parameters of the Halfar solution.
  * `A`: Glen's law parameter.
  * `n`: Creep exponent.
  * `physical_parameters::PhysicalParameters`: Physical parameters that allow   retrieving the ice density and the gravity constant.
