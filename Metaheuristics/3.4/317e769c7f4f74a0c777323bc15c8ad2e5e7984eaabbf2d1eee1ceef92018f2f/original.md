```
mcdm(fs, w, method)
```

Perform selected `method` for a given `fs` and weight vector. Here, `fs` can be a set of non-dominated solutions (population), a `State` or a decision matrix.

Also, `method` can be selected from `JMcDM` package.

Supported McDM methods:

  * `ArasMethod`
  * `CocosoMethod`
  * `CodasMethod`
  * `CoprasMethod`
  * `EdasMethod`
  * `ElectreMethod`
  * `GreyMethod`
  * `MabacMethod`
  * `MaircaMethod`
  * `MooraMethod`
  * `SawMethod`
  * `TopsisMethod` **(default method)**
  * `VikorMethod`
  * `WPMMethod`
  * `WaspasMethod`
  * `MarcosMethod`
  * `ROVMethod`

### Example 1:

Performing McDM using a population.

```julia-repl
julia> using JMcDM

julia> _, _, population = Metaheuristics.TestProblems.ZDT1();

julia> dm = mcdm(population, [0.5, 0.5], TopsisMethod());

julia> population[dm.bestIndex]
(f = [0.5353535353535354, 0.2683214262030523], g = [0.0], h = [0.0], x = [5.354e-01, 0.000e+00, …, 0.000e+00])
```

### Example 2:

Performing McDM using results from metaheuristic.

```julia-repl
julia> using JMcDM

julia> f, bounds, _ = Metaheuristics.TestProblems.ZDT1();

julia> res = optimize(f, bounds, NSGA2());

julia> dm = mcdm(res, [0.5, 0.5], TopsisMethod());

julia> res.population[dm.bestIndex]
(f = [0.32301132058506055, 0.43208538139854685], g = [0.0], h = [0.0], x = [3.230e-01, 1.919e-04, …, 1.353e-04])
```
