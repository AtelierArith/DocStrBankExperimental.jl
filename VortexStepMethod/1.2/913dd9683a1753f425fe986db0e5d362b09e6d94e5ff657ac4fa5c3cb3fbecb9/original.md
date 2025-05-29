```
solve(solver::Solver, body_aero::BodyAerodynamics, gamma_distribution=nothing; 
      log=false, reference_point=zeros(MVec3))
```

Main solving routine for the aerodynamic model. Reference point is in the kite body (KB) frame. See also: [solve!](@ref)

# Arguments:

  * solver::Solver: The solver to use, could be a VSM or LLT solver. See: [Solver](@ref)
  * body_aero::BodyAerodynamics: The aerodynamic body. See: [BodyAerodynamics](@ref)
  * gamma_distribution: Initial circulation vector or nothing; Length: Number of segments. [m²/s]

# Keyword Arguments:

  * log=false: If true, print the number of iterations and other info.
  * reference_point=zeros(MVec3)

# Returns

A dictionary with the results.
