```
lp_sensitivity_report(model::Model; atol::Float64 = 1e-8)::SensitivityReport
```

Given a linear program `model` with a current optimal basis, return a [`SensitivityReport`](@ref) object, which maps:

  * Every variable reference to a tuple `(d_lo, d_hi)::Tuple{Float64,Float64}`, explaining how much the objective coefficient of the corresponding variable can change by, such that the original basis remains optimal.
  * Every constraint reference to a tuple `(d_lo, d_hi)::Tuple{Float64,Float64}`, explaining how much the right-hand side of the corresponding constraint can change by, such that the basis remains optimal.

Both tuples are relative, rather than absolute. So given a objective coefficient of `1.0` and a tuple `(-0.5, 0.5)`, the objective coefficient can range between `1.0 - 0.5` an `1.0 + 0.5`.

`atol` is the primal/dual optimality tolerance, and should match the tolerance of the solver used to compute the basis.

Note: interval constraints are NOT supported.

# Example

```
model = Model(HiGHS.Optimizer)
@variable(model, -1 <= x <= 2)
@objective(model, Min, x)
optimize!(model)
report = lp_sensitivity_report(model; atol = 1e-7)
dx_lo, dx_hi = report[x]
println(
    "The objective coefficient of `x` can decrease by $dx_lo or " *
    "increase by $dx_hi."
)
c = LowerBoundRef(x)
dRHS_lo, dRHS_hi = report[c]
println(
    "The lower bound of `x` can decrease by $dRHS_lo or increase " *
    "by $dRHS_hi."
)
```
