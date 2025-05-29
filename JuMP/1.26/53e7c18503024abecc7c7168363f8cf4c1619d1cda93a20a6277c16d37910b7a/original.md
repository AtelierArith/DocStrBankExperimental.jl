```
lp_sensitivity_report(model::GenericModel{T}; atol::T = Base.rtoldefault(T))::SensitivityReport{T} where {T}
```

Given a linear program `model` with a current optimal basis, return a [`SensitivityReport`](@ref) object, which maps:

  * Every variable reference to a tuple `(d_lo, d_hi)::Tuple{T,T}`, explaining how much the objective coefficient of the corresponding variable can change by, such that the original basis remains optimal.
  * Every constraint reference to a tuple `(d_lo, d_hi)::Tuple{T,T}`, explaining how much the right-hand side of the corresponding constraint can change by, such that the basis remains optimal.

Both tuples are relative, rather than absolute. So given a objective coefficient of `1.0` and a tuple `(-0.5, 0.5)`, the objective coefficient can range between `1.0 - 0.5` an `1.0 + 0.5`.

`atol` is the primal/dual optimality tolerance, and should match the tolerance of the solver used to compute the basis.

Note: interval constraints are NOT supported.

## Example

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, -1 <= x <= 2)
x

julia> @objective(model, Min, x)
x

julia> optimize!(model)

julia> report = lp_sensitivity_report(model; atol = 1e-7);

julia> dx_lo, dx_hi = report[x]
(-1.0, Inf)

julia> println(
           "The objective coefficient of `x` can decrease by $dx_lo or " *
           "increase by $dx_hi."
       )
The objective coefficient of `x` can decrease by -1.0 or increase by Inf.

julia> dRHS_lo, dRHS_hi = report[LowerBoundRef(x)]
(-Inf, 3.0)

julia> println(
           "The lower bound of `x` can decrease by $dRHS_lo or increase " *
           "by $dRHS_hi."
       )
The lower bound of `x` can decrease by -Inf or increase by 3.0.
```
