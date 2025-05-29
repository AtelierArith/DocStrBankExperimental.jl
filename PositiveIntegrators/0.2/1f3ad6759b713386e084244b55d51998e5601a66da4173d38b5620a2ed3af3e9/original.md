```
work_precision_adaptive(prob, algs, labels, abstols, reltols, alg_ref;
                        adaptive_ref = false,
                        abstol_ref = 1e-14,
                        reltol_ref = 1e-13,
                        compute_error = rel_max_error_tend,
                        seconds = 2,
                        numruns = 20,
                        kwargs...)
```

Returns a dictionary to create work-precision diagrams. The problem `prob` is solved by each algorithm in `algs` for all tolerances defined in `abstols` and `reltols`. For the respective tolerances the error and computing time are stored in the dictionary. If the solve is not successful for the given tolerances, then `(Inf, Inf)` is stored in the dictionary. The strings in the array `labels` are used as keys of the dictionary. The reference solution used for error computations is computed with the algorithm `alg_ref`. Additional keyword arguments are passed on to `solve`.

### Keyword arguments:

  * `adaptive_ref`: If `true` the refenerce solution is computed adaptively with tolerances `abstol_ref` and `reltol_ref`. Otherwise $10^5$ steps are used.
  * `abstol_ref`: See `adaptive_ref`.
  * `reltol_ref`: See `adaptive_ref`.
  * `compute_error(sol::ODESolution, ref_sol::ODESolution)`: A function to compute the error between `sol` and `ref_sol`.
  * `seconds`: If the measured computing time of a single solve is larger than `seconds`, then this computing time is stored in the dictionary.
  * `numruns`: If the measured computing time of a single solve is less than or equal to `seconds`, then `numruns` solves are performed and the median of the respective computing times is stored in the dictionary.
