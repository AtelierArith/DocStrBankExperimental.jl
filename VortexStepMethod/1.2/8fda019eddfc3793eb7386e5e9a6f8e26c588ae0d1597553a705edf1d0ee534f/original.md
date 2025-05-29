```
solve!(solver::Solver, body_aero::BodyAerodynamics, gamma_distribution=solver.sol.gamma_distribution; 
      log=false, reference_point=zeros(MVec3), moment_frac=0.1)
```

Main solving routine for the aerodynamic model. Reference point is in the kite body (KB) frame. This version is modifying the `solver.sol` struct and is faster than the `solve` function which returns a dictionary.

# Arguments:

  * solver::Solver: The solver to use, could be a VSM or LLT solver. See: [Solver](@ref)
  * body_aero::BodyAerodynamics: The aerodynamic body. See: [BodyAerodynamics](@ref)
  * gamma_distribution: Initial circulation vector or nothing; Length: Number of segments. [m²/s]

# Keyword Arguments:

  * log=false: If true, print the number of iterations and other info.
  * reference_point=zeros(MVec3)
  * moment_frac=0.1: X-coordinate of normalized panel around which the moment distribution should be calculated.

# Returns

The solution of type [VSMSolution](@ref)
