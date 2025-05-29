```
@objective(model::Model, sense, func)
```

Set the objective sense to `sense` and objective function to `func`. The objective sense can be either `Min`, `Max`, `MathOptInterface.MIN_SENSE`, `MathOptInterface.MAX_SENSE` or `MathOptInterface.FEASIBILITY_SENSE`; see [`MathOptInterface.ObjectiveSense`](https://jump.dev/MathOptInterface.jl/stable/reference/models/#MathOptInterface.ObjectiveSense). In order to set the sense programmatically, i.e., when `sense` is a Julia variable whose value is the sense, one of the three `MathOptInterface.ObjectiveSense` values should be used. The function `func` can be a single JuMP variable, an affine expression of JuMP variables or a quadratic expression of JuMP variables.

## Examples

To minimize the value of the variable `x`, do as follows:

```jldoctest @objective; setup = :(using JuMP)
julia> model = Model()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> @variable(model, x)
x

julia> @objective(model, Min, x)
x
```

To maximize the value of the affine expression `2x - 1`, do as follows:

```jldoctest @objective
julia> @objective(model, Max, 2x - 1)
2 x - 1
```

To set a quadratic objective and set the objective sense programmatically, do as follows:

```jldoctest @objective
julia> sense = MIN_SENSE
MIN_SENSE::OptimizationSense = 0

julia> @objective(model, sense, x^2 - 2x + 1)
x² - 2 x + 1
```
