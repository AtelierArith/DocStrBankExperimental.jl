Constructs an `LPModel` for the LP problem.

# Arguments

  * `A`: Constraint matrix
  * `b`: Right-hand side vector
  * `c`: Cost vector
  * `ε`: Relaxation constant
  * `λ`: Feasibility constant
  * `maximize`: If `true`, solves max ⟨c, x⟩
  * `kwargs`: Additional keyword arguments

# Returns

An instance of `LPModel`.
