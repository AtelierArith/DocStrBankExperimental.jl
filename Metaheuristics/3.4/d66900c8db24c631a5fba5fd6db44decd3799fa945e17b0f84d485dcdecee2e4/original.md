```
convergence(state)
```

get the data (touple with the number of function evaluations and fuction values) to plot the convergence graph. 

# Example

```jldoctest
julia> f(x) = sum(x.^2)
f (generic function with 1 method)

julia> bounds = [  -10.0 -10 -10; # lower bounds
                    10.0  10 10 ] # upper bounds
2×3 Array{Float64,2}:
 -10.0  -10.0  -10.0
  10.0   10.0   10.0

julia> state = optimize(f, bounds, ECA(options=Options(store_convergence=true)))
+=========== RESULT ==========+
| Iter.: 1022
| f(x) = 7.95324e-163
| solution.x = [-7.782044850211721e-82, 3.590044165897827e-82, -2.4665318114710003e-82]
| f calls: 21469
| Total time: 0.3300 s
+============================+

julia> n_fes, fxs = convergence(state);
```
