`solve(system::ODESystem, timespan; solver=AutoVern9(Rodas5())`

Return the solution of the `system` ODE system in the `timespan` interval (for the available different ODE system solvers, see the documentation of `DifferentialEquations.jl`).

We use the AutoVern9(Rodas5()) solver since it is among the suggested ones in the documentation of `DifferentialEquations.jl`, and among those we tested, it is the one that works best.
