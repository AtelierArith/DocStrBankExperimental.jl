```julia
v, M = optimize([(f, set) ...], X, d)
```

Solve the moment program of relaxation of order `d` in the variables `X`, defined by the constraint or objective paires `(f, set)` where `f` is a polynomial and `set` is a string

  * "inf", "sup" to define the objective.
  * "=0" to define zero constraints:
  * ">=0", "<=0" to define sign constraints

It outputs

  * v: the optimal value
  * M: the optimized moment program of type MOM.Model

## Example

```julia
using MomentPolynomialOpt

X  = @polyvar x1 x2
e1 = x1^2-2
e2 = (x2^2-3)*(x1*x2-2)
p1 = x1
p2 = 2-x2
v, M = optimize([(-x1, "inf"), (e1, "=0"), (e2, "=0"), (p1, ">=0"), (p2>=0)], X, 3)
```

To recover the optimal values, see [`get_minimizers`](@ref), [`get_measure`](@ref), [`get_series`](@ref).
