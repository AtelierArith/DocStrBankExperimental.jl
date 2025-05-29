Termination(;abstol::Real=10^-9,             reltol::Real=10^-9,             rlx*abstol::Real=10^-9,             rlx*reltol::Real=10^-9,             time*limit::Real=Inf,             max*iter::Int=typemax(Int),             inttol::Real=10^-8,             allow*frac::Symbol=:binary*solve)

Define the stopping conditions for `JuDGE.solve()` / `JuDGE.branch_and_price()`.

### Optional Arguments

`abstol` is the absolute tolerance for the best integer-feasible objective value and the lower bound.

`reltol` is the relative tolerance for the best integer-feasible objective value and the lower bound.

`rlx_abstol` is the absolute tolerance for the relaxed master objective value and the lower bound.

`rlx_reltol` is the relative tolerance for the relaxed master objective value and the lower bound.

`time_limit` is the maximum duration in seconds.

`max_iter` is the maximum number of iterations.

`inttol` is the maximum deviation from 0 or 1 for any binary/integer variable for integer feasible solutions.

`allow_frac` indicates whether a fractional solution will be returned; possible values are:     `:binary_solve` a binary solve of master will be performed (if needed) prior to the solution being returned;     `:binary_solve_return_relaxation` a binary solve of master will be performed (if needed), updating the upper bound,     but the master problem relation will be returned;     `:first_fractional` will return the first fractional master solution found;     `:no_binary_solve` will simply return the solution to the relaxed master problem when terminated.

### Examples

Termination(rlx_abstol=10^-6)    Termination(abstol=10^-3,inttol=10^-6)
