```julia
equation_dependencies(sys::AbstractSystem; variables = states(sys))
```

Given an `AbstractSystem` calculate for each equation the variables it depends on.

Notes:

  * Variables that are not in `variables` are filtered out.
  * `get_variables!` is used to determine the variables within a given equation.
  * returns a `Vector{Vector{Variable}}()` mapping the index of an equation to the `variables` it depends on.

Example:

```julia
using ModelingToolkit
@parameters β γ κ η
@variables t S(t) I(t) R(t)

rate₁ = β * S * I
rate₂ = γ * I + t
affect₁ = [S ~ S - 1, I ~ I + 1]
affect₂ = [I ~ I - 1, R ~ R + 1]
j₁ = ModelingToolkit.ConstantRateJump(rate₁, affect₁)
j₂ = ModelingToolkit.VariableRateJump(rate₂, affect₂)

# create a JumpSystem using these jumps
@named jumpsys = JumpSystem([j₁, j₂], t, [S, I, R], [β, γ])

# dependency of each jump rate function on state variables
equation_dependencies(jumpsys)

# dependency of each jump rate function on parameters
equation_dependencies(jumpsys, variables = parameters(jumpsys))
```
