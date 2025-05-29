```
variable(core, dims...; start = 0, lvar = -Inf, uvar = Inf)
```

Adds variables with dimensions specified by `dims` to `core`, and returns `Variable` object. `dims` can be either `Integer` or `UnitRange`.

## Keyword Arguments

  * `start`: The initial guess of the solution. Can either be `Number`, `AbstractArray`, or `Generator`.
  * `lvar` : The variable lower bound. Can either be `Number`, `AbstractArray`, or `Generator`.
  * `uvar` : The variable upper bound. Can either be `Number`, `AbstractArray`, or `Generator`.

## Example

```jldoctest
julia> using ExaModels

julia> c = ExaCore();

julia> x = variable(c, 10; start = (sin(i) for i=1:10))
Variable

  x ∈ R^{10}

julia> y = variable(c, 2:10, 3:5; lvar = zeros(9,3), uvar = ones(9,3))
Variable

  x ∈ R^{9 × 3}

```
