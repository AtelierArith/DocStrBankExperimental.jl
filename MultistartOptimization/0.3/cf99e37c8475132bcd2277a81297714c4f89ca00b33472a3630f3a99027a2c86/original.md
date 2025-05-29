```julia
multistart_minimization(
    multistart_method,
    local_method,
    minimization_problem;
    use_threads,
    prepend_points
)

```

Solve `minimization_problem` by using `local_method` within `multistart_method`.

When `use_threads`, initial point search is parallelized using `Threads.@spawn`.

`prepend_points` should contain a vector of initial starting points that are prepended to the Sobol sequence. These are useful if a guess is available for the vicinity of the optimum.
