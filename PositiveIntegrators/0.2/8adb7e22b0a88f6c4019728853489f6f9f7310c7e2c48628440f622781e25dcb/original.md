```
work_precision_fixed(prob, algs, labels, dts, alg_ref;
                     compute_error = rel_max_error_tend,
                     seconds = 2,
                     numruns = 20)
```

Returns a dictionary to create work-precision diagrams. The problem `prob` is solved by each algorithm in `algs` for all the step sizes defined in `dts`. For each step size the error and computing time are stored in the dictionary. If the solve is not successful for a given step size, then `(Inf, Inf)` is stored in the dictionary. The strings in the array `labels` are used as keys of the dictionary. The reference solution used for error computations is computed with the algorithm `alg_ref`.

### Keyword arguments:

  * `compute_error(sol::ODESolution, ref_sol::ODESolution)`: Function to compute the error between `sol` and `ref_sol`.
  * `seconds`: If the measured computing time of a single solve is larger than `seconds`, then this computing time is stored in the dictionary.
  * `numruns`: If the measured computing time of a single solve is less than or equal to `seconds`, then `numruns` solves are performed and the median of the respective computing times is stored in the dictionary.
