```
struct NonlinearCombinatorialInstance <: CombinatorialInstance
```

A nonlinear combinatorial-optimisation problem. Such a problem is built on top  of a linear problem, `combinatorial_structure`, providing all the constants  required for the problem (e.g., a graph); rewards from this object are ignored. The optimisation sense is given by this object (i.e., minimise or maximise).

The nonlinearity is only contained in the nonlinear objective function,  supposed to have the following expression: 

$a^T x + f(b^T x)$

where $a$ is encoded as `linear_coefficients` and $b$ as  `nonlinear_coefficients`. The function `f` is indicated by  `nonlinear_function`, currently a value of the enumeration `NonlinearFunction`.

`ε` is a parameter often used for nonlinear instances indicating the (additive) precision at which the problem should be solved.
