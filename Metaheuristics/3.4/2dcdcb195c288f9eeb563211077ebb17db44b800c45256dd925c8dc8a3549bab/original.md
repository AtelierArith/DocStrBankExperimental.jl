```
best_alternative(res, w, method)
```

Perform McDM using results from metaheuristic and return best alternative in `res.population`.

### Example

```julia-repl
julia> f, bounds, _ = Metaheuristics.TestProblems.ZDT1();

julia> res = optimize(f, bounds, NSGA2());

julia> best_sol = best_alternative(res, [0.5, 0.5], TopsisMethod())
(f = [0.32301132058506055, 0.43208538139854685], g = [0.0], h = [0.0], x = [3.230e-01, 1.919e-04, …, 1.353e-04])
```
