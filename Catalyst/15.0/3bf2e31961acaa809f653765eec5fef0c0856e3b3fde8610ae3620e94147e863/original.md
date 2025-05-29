```julia
JumpInputs(rs::ReactionSystem, u0, tspan,
            p = DiffEqBase.NullParameters;
            name = nameof(rs),
            combinatoric_ratelaws = get_combinatoric_ratelaws(rs),
            checks = false, physical_scales = nothing, 
            expand_catalyst_funs = true, 
            save_positions = (true, true),
            remake_warn = true, kwargs...)
```

Constructs the input to build a JumpProblem for the given reaction system.

Keyword args and default values:

  * `combinatoric_ratelaws=true` uses factorial scaling factors in calculating the rate law, i.e. for `2S -> 0` at rate `k` the ratelaw would be `k*S*(S-1)/2!`. Set `combinatoric_ratelaws=false` for a ratelaw of `k*S*(S-1)`, i.e. the scaling factor is ignored. Defaults to the value given when the `ReactionSystem` was constructed (which itself defaults to true).
  * `expand_catalyst_funs = true`, replaces Catalyst defined functions like `hill(A,B,C,D)` with their rational function representation when converting to another system type. Set to `false`` to disable.
  * `remake_warn = true`, if `true`, a warning is thrown if the system includes ODEs, variable rate jumps, or continuous events. This is because `remake` does not work for such problems, and instead both `JumpInputs` and then `JumpProblem` must be called again if one wishs to change any parameter or initial condition values. This warning can be disabled by passing `remake_warn = false`.
  * `save_positions = (true, true)`, indicates whether for any reaction classified as a `VariableRateJump` whether to save the solution before and/or after the jump occurs. Defaults to true for both.

Example:

```julia
using Catalyst, OrdinaryDiffEqTsit5, JumpProcesses, Plots
rn = @reaction_network begin
    k*(1 + sin(t)), 0 --> A
end
jinput = JumpInputs(rn, [:A => 0], (0.0, 10.0), [:k => .5])
@assert jinput.prob isa ODEProblem
jprob = JumpProblem(jinput)
sol = solve(jprob, Tsit5())
plot(sol, idxs = :A)

rn = @reaction_network begin
    k, 0 --> A
end
jinput = JumpInputs(rn, [:A => 0], (0.0, 10.0), [:k => .5])
@assert jinput.prob isa DiscreteProblem
jprob = JumpProblem(jinput)
sol = solve(jprob)
plot(sol, idxs = :A)
```
