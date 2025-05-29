breakpoints(pwl, ε = 1e-5)

Outputs the breakpoints needed for several solvers (CPLEX, Gurobi,...) to natively model PWL functions. 

# Arguments

  * `plw` : pwl function
  * `ε` : numerical precision used to detect if the end endpoints of two segments are equal (to detect discontinuities)
