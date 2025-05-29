```julia
struct MassActionJump{T, S, U, V} <: DiffEqJump.AbstractMassActionJump
```

Optimized representation for `ConstantRateJump`s that can be represented in mass action form, offering improved performance within jump algorithms compared to `ConstantRateJump`. For detailed examples and usage information see the

  * [Main Docs](https://jump.sciml.ai/stable/jump_types/#Defining-a-Mass-Action-Jump)
  * [Tutorial](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)

### Constructors

  * `MassActionJump(reactant_stoich, net_stoich; scale_rates=true, param_idxs=nothing)`

Here `reactant_stoich` denotes the reactant stoichiometry for each reaction and `net_stoich` the net stoichiometry for each reaction.

## Fields

  * `scaled_rates`: The (scaled) reaction rate constants.
  * `reactant_stoch`: The reactant stoichiometry vectors.
  * `net_stoch`: The net stoichiometry vectors.
  * `param_mapper`: Parameter mapping functor to identify reaction rate constants with parameters in `p` vectors.

## Keyword Arguments

  * `scale_rates=true`, whether to rescale the reaction rate constants according to the stoichiometry.
  * `nocopy=false`, whether the `MassActionJump` can alias the `scaled_rates` and `reactant_stoch` from the input. Note, if `scale_rates=true` this will potentially modify both of these.
  * `param_idxs=nothing`, indexes in the parameter vector, `JumpProblem.prob.p`, that correspond to each reaction's rate.

See the tutorial and main docs for details.

## Examples

An SIR model with `S + I --> 2I` at rate β as the first reaction and `I --> R` at rate ν as the second reaction can be encoded by

```julia
p        = (β=1e-4, ν=.01)
u0       = [999, 1, 0]       # (S,I,R)
tspan    = (0.0, 250.0)
rateidxs = [1, 2]           # i.e. [β,ν]
reactant_stoich =
[
  [1 => 1, 2 => 1],         # 1*S and 1*I
  [2 => 1]                  # 1*I
]
net_stoich =
[
  [1 => -1, 2 => 1],        # -1*S and 1*I
  [2 => -1, 3 => 1]         # -1*I and 1*R
]
maj = MassActionJump(reactant_stoich, net_stoich; param_idxs=rateidxs)
prob = DiscreteProblem(u0, tspan, p)
jprob = JumpProblem(prob, Direct(), maj)
```

## Notes

  * By default reaction rates are rescaled when constructing the `MassActionJump` as explained in the [main docs](https://jump.sciml.ai/stable/jump_types/#Defining-a-Mass-Action-Jump). Disable this with the kwarg `scale_rates=false`.
  * Also see the [main docs](https://jump.sciml.ai/stable/jump_types/#Defining-a-Mass-Action-Jump) for how to specify reactions with no products or no reactants.
