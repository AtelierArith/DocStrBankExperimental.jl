```
State datatype
```

State is used to store the current metaheuristic status. In fact, the `optimize` function returns a `State`.

  * `best_sol` Stores the best solution found so far.
  * `population` is an Array{typeof(best_sol)} for population-based algorithms.
  * `f_calls` is the number of objective functions evaluations.
  * `g_calls`  is the number of inequality constraints evaluations.
  * `h_calls` is the number of equality constraints evaluations.
  * `iteration` is the current iteration.
  * `success_rate` percentage of new generated solutions better that their parents.
  * `convergence` used save the `State` at each iteration.
  * `start_time` saves the `time()` before the optimization process.
  * `final_time` saves the `time()` after the optimization process.
  * `stop` if true, then stops the optimization process.

# Example

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # lower bounds
                    10.0  10 10 ] # upper bounds
2×3 Array{Float64,2}:
 -10.0  -10.0  -10.0
  10.0   10.0   10.0

julia> state = optimize(f, bounds)
+=========== RESULT ==========+
| Iter.: 1009
| f(x) = 7.16271e-163
| solution.x = [-7.691251412064516e-83, 1.0826961235605951e-82, -8.358428300092186e-82]
| f calls: 21190
| Total time: 0.2526 s
+============================+

julia> minimum(state)
7.162710802659093e-163

julia> minimizer(state)
3-element Array{Float64,1}:
 -7.691251412064516e-83
  1.0826961235605951e-82
 -8.358428300092186e-82
```
