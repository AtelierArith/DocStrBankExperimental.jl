support*function(h::AbstractVector, rep::Rep, solver=Polyhedra.linear*objective_solver(p))

Return the value of the support function of `rep` at `h`. See [Section 13, R15] for more details.

[R15] Rockafellar, R.T. *Convex analysis*. Princeton university press, **2015**.
