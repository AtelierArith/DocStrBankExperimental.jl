```julia
v, M = optimize(sense, f, [e1, e2, ...], [p1, p2, ...], X, d)
```

Compute the optimum of `f` under the constraints $e_i$ =0 and $p_i \geq 0$ using a relaxation of order `d` on the moments in the variable `X`. 

  * $f, e_i, p_i$ should be polynomials in the variables X.
  * 'sense` is a Symbol in [:Inf, :inf, :Min,:min]  or :Sup, :sup, :Max, :max
  * `X` is a tuple of variables
  * `d` is the order of the relaxation
  * `optimizer`is the optimizer used to solve the moment relaxation. By default it is `MMT[:optimizer]`.

If the problem is feasible and has minimizers, it outputs

  * v: the optimum value
  * M: the moment model of type JuMP.Model

## Example

```julia
using MomentPolynomialOpt

X  = @polyvar x1 x2
e1 = x1^2-2
e2 = (x2^2-3)*(x1*x2-2)
p1 = x1
p2 = 2-x2
v, M = optimize(:inf, -x1, [e1, e2], [p1, p2], X, 3)
```

To recover the optimizers, see [`get_minimizers`](@ref), [`get_measure`](@ref), [`get_series`](@ref).
