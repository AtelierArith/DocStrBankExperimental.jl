```
solve_problems(solver, solver_name, problems; kwargs...)
```

Apply a solver to a set of problems.

#### Arguments

  * `solver`: the function name of a solver;
  * `solver_name`: name of the solver;
  * `problems`: the set of problems to pass to the solver, as an iterable of `AbstractNLPModel`. It is recommended to use a generator expression (necessary for CUTEst problems).

#### Keyword arguments

  * `solver_logger::AbstractLogger`: logger wrapping the solver call (default: `NullLogger`);
  * `reset_problem::Bool`: reset the problem's counters before solving (default: `true`);
  * `skipif::Function`: function to be applied to a problem and return whether to skip it (default: `x->false`);
  * `colstats::Vector{Symbol}`: summary statistics for the logger to output during the

benchmark (default: `[:name, :nvar, :ncon, :status, :elapsed_time, :objective, :dual_feas, :primal_feas]`);

  * `info_hdr_override::Dict{Symbol,String}`: header overrides for the summary statistics (default: use default headers);
  * `prune`: do not include skipped problems in the final statistics (default: `true`);
  * any other keyword argument to be passed to the solver.

#### Return value

  * a `DataFrame` where each row is a problem, minus the skipped ones if `prune` is true.
