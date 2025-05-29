```
stats = bmark_results_to_dataframes(results)
```

Convert `PkgBenchmark` results to a dictionary of `DataFrame`s. The benchmark SUITE should have been constructed in the form

```
SUITE[solver][case] = ...
```

where `solver` will be recorded as one of the solvers to be compared in the DataFrame and case is a test case. For example:

```
SUITE["CG"]["BCSSTK09"] = @benchmarkable ...
SUITE["LBFGS"]["ROSENBR"] = @benchmarkable ...
```

Inputs:

  * `results::BenchmarkResults`: the result of `PkgBenchmark.benchmarkpkg`

Output:

  * `stats::Dict{Symbol,DataFrame}`: a dictionary of `DataFrame`s containing the   benchmark results per solver.
