```
solve(f; options...)
solve(f, start_solutions; start_parameters, target_parameters, options...)
solve(f, start_solutions; start_subspace, target_subspace, options...)
solve(g, f, start_solutions; options...)
solve(homotopy, start_solutions; options...)
```

Solve the given problem. If only a single polynomial system `f` is given, then all (complex) isolated solutions are computed. If a system `f` depending on parameters together with start and target parameters is given then a parameter homotopy is performed. If two systems `g` and `f` with solutions of `g` are given then the solutions are tracked during the deformation of `g` to `f`. Similarly, for a given homotopy `homotopy` $H(x,t)$ with solutions at $t=1$ the solutions at $t=0$ are computed. See the documentation for examples. If the input is a *homogeneous* polynomial system, solutions on a random affine chart of projective space are computed.

## General Options

The `solve` routines takes the following options:

  * `catch_interrupt = true`: If this is `true`, the computation is gracefully stopped and a partial result is returned when the computation is interruped.
  * `compile = mixed`: If `true` then a `System` (resp. `Homotopy`) is compiled to a straight line program ([`CompiledSystem`](@ref) resp. [`CompiledHomotopy`](@ref)) for evaluation. This induces a compilation overhead. If `false` then the generated program is only interpreted ([`InterpretedSystem`](@ref) resp. [`InterpretedHomotopy`](@ref)). This is slower than the compiled version, but does not introduce compilation overhead.
  * `endgame_options`: The options and parameters for the endgame. See [`EndgameOptions`](@ref).
  * `seed`: The random seed used during the computations. The seed is also reported in the result. For a given random seed the result is always identical.
  * `show_progress= true`: Indicate whether a progress bar should be displayed.
  * `stop_early_cb`: Here it is possible to provide a function (or any callable struct) which accepts a `PathResult` `r` as input and returns a `Bool`. If `stop_early_cb(r)` is `true` then no further paths are tracked and the computation is finished. This is only called for successfull paths. This is for example useful if you only want to compute one solution of a polynomial system. For this `stop_early_cb = _ -> true` would be sufficient.
  * `threading = true`: Enable multi-threading for the computation. The number of available threads is controlled by the environment variable `JULIA_NUM_THREADS`.  Careful: Some CPUs hang when using multiple threads. To avoid this run Julia with 1  interactive thread for the REPL and `n` threads for other tasks (e.g., `julia -t 8,1` for `n=8`).
  * `tracker_options`: The options and parameters for the path tracker. See [`TrackerOptions`](@ref).

## Options depending on input

If only a polynomial system is given:

  * `start_system`: Possible values are `:total_degree` and `:polyhedral`. Depending on the choice furhter options are possible. See also [`total_degree`](@ref) and [`polyhedral`](@ref).

If a system `f` depending on parameters together with start parameters (or start subspace), start solutions and *multiple* target parameters (or target subspaces) then the following options are also available:

  * `flatten`: Flatten the output of `transform_result`. This is useful for example if  `transform_result` returns a vector of solutions, and you only want a single vector of  solutions as the result (instead of a vector of vector of solutions).
  * `transform_parameters = identity`: Transform a parameters values `p` before passing it to `target_parameters = ...`.
  * `transform_result`: A function taking two arguments, the `result` and the parameters `p`. By default this returns the tuple `(result, p)`.

## Basic example

```julia-repl
julia> @var x y;

julia> F = System([x^2+y^2+1, 2x+3y-1])
System of length 2
 2 variables: x, y

 1 + x^2 + y^2
 -1 + 2*x + 3*y

julia> solve(F)
Result with 2 solutions
=======================
• 2 non-singular solutions (0 real)
• 0 singular solutions (0 real)
• 2 paths tracked
• random seed: 0x75a6a462
• start_system: :polyhedral
```
