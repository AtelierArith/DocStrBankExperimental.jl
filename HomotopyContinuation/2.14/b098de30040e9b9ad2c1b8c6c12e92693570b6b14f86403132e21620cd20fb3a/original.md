```
monodromy_solve(F, [sols, p]; options..., tracker_options = TrackerOptions())
```

Solve a polynomial system `F(x;p)` with specified parameters and initial solutions `sols` by monodromy techniques. This makes loops in the parameter space of `F` to find new solutions. If `F` the parameters `p` only occur *linearly* in `F` it is eventually possible to compute a *start pair* $(x₀, p₀)$ automatically. In this case `sols` and `p` can be omitted and the automatically generated parameters can be obtained with the [`parameters`](@ref) function from the [`MonodromyResult`](@ref).

```
monodromy_solve(F, [sols, L]; dim, codim, intrinsic = nothing, options...,
                              tracker_options = TrackerOptions())
```

Solve the polynomial system `[F(x); L(x)] = 0` where `L` is a `[LinearSubspace`](@ref). If `sols` and `L` are not provided it is necesary to provide `dim` or `codim` where `(co)dim` is the expected (co)dimension of a component of `V(F)`. See also [`linear_subspace_homotopy`](@ref) for the `intrinsic` option.

## Options

  * `catch_interrupt = true`: If true catches interruptions (e.g. issued by pressing Ctrl-C) and returns the partial result.
  * `check_startsolutions = true`: If `true`, we do a Newton step for each entry of `sols`for checking if it is a valid startsolutions. Solutions which are not valid are sorted out.
  * `compile = mixed`: If `true` then a `System` (resp. `Homotopy`) is compiled to a straight line program ([`CompiledSystem`](@ref) resp. [`CompiledHomotopy`](@ref)) for evaluation. This induces a compilation overhead. If `false` then the generated program is only interpreted ([`InterpretedSystem`](@ref) resp. [`InterpretedHomotopy`](@ref)). This is slower than the compiled version, but does not introduce compilation overhead.
  * `distance = EuclideanNorm()`: The distance function used for [`UniquePoints`](@ref).
  * `loop_finished_callback = always_false`: A callback to end the computation. This function is called with all current [`PathResult`](@ref)s after a loop is exhausted. 2 arguments. Return `true` if the compuation should be stopped.
  * `equivalence_classes=true`: This only applies if there is at least one group action supplied. We then consider two solutions in the same equivalence class if we can transform one to the other by the supplied group actions. We only track one solution per equivalence class.
  * `group_action = nothing`: A function taking one solution and returning other solutions if there is a constructive way to obtain them, e.g. by symmetry.
  * `group_actions = nothing`: If there is more than one group action you can use this to chain the application of them. For example if you have two group actions `foo` and `bar` you can set `group_actions=[foo, bar]`. See [`GroupActions`](@ref) for details regarding the application rules.
  * `max_loops_no_progress = 5`: The maximal number of iterations (i.e. loops generated) without any progress.
  * `min_solutions`: The minimal number of solutions before a stopping heuristic is applied. By default no lower limit is enforced.
  * `parameter_sampler = independent_normal`: A function taking the parameter `p` and returning a new random parameter `q`. By default each entry of the parameter vector is drawn independently from Normal distribution.
  * `permutations = false`: Whether to keep track of the permutations induced by the loops.
  * `resuse_loops = :all`: Strategy to reuse other loops for new found solutions. `:all` propagates a new solution through all other loops, `:random` picks a random loop, `:none` doesn't reuse a loop.
  * `target_solutions_count`: The computation is stopped if this number of solutions is reached.
  * `threading = true`: Enable multithreading of the path tracking. Careful: Some CPUs hang when using multiple threads. To avoid this run Julia with 1  interactive thread for the REPL and `n` threads for other tasks (e.g., `julia -t 8,1` for `n=8`).
  * `timeout`: The maximal number of *seconds* the computation is allowed to run.
  * `trace_test = true`: If `true` a trace test is performed to check whether all solutions are found. This is only applicable if monodromy is performed with a linear subspace. See also [`trace_test`](@ref).
  * `trace_test_tol = 1e-10`: The tolerance for the trace test to be successfull. The trace is divided by the number of solutions before compared to the trace*test*tol.
  * `unique_points_rtol`: the relative tolerance for [`unique_points`](@ref).
  * `unique_points_atol`: the absolute tolerance for [`unique_points`](@ref).
