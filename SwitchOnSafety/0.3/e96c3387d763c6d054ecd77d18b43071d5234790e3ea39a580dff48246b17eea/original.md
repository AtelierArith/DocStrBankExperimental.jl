```
invariant_sets(system::AbstractHybridSystem, optimizer_constructor,
               set_variables::AbstractVector{<:SetProg.AbstractVariable};
               volume_heuristic = nth_root,
               infeasibility_certificates = nothing,
               verbose=1,
               λ=Dict{transitiontype(system), Float64}(),
               enabled = states(system))
```

Compute maximal invariant sets of the family `set_variables` for the modes of `system` using the solver provided by `optimizer_constructor`. The volume of the sets is estimated using `volume_heuristic`. If the program is infeasible, the certificates for each transition are stored in `infeasibility_certificates`. For the containment of non-homogeneous, the S-procedure might be a Bilinear Matrix Inequality (BMI) which is NP-hard to solve. To avoid that, provides the value of `λ` to use in the dictionary `λ`. To ignore some state and the transitions involving these states in the computation, give an `enabled` vector without them.
