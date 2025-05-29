```julia
DiffEqBase.JumpProblem(js::JumpSystem, prob, aggregator; kwargs...)
```

JumpSystemからJumpProblemを生成します。

[`DiscreteProblem`](@ref)の定義からの例を続けます：

```julia
jprob = JumpProblem(js, dprob, Direct())
sol = solve(jprob, SSAStepper())
```
