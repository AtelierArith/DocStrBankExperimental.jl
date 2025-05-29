```
sim_cfbd(t  ::Float64,
         λ  ::Float64,
         μ  ::Float64,
         ψ  ::Vector{Float64},
         ψts::Vector{Float64})
```

Simulate a constant fossilized birth-death `iTree` of height `t` with speciation rate `λ`, extinction rate `μ` and a vector of fossilization rates `ψ`.
