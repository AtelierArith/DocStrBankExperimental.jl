```
set_user_solutions!(optimizer, x, fx;verbose=true)
```

Provide initial solutions to the `optimizer`.

  * `x` can be a `Vector` and `fx` a function or `fx = f(x)`
  * `x` can be a matrix containing solutions in rows.

### Example

```julia-repl
julia> f(x) = abs(x[1]) + x[2]  + x[3]^2 # objective function
f (generic function with 1 method)

julia> algo  = ECA(N = 61); # optimizer

julia> # one solution can be provided
       x0 = [0.5, 0.5, 0.5];

julia> set_user_solutions!(algo, x0, f);

julia> # providing multiple solutions
       X0 = rand(30, 3); # 30 solutions with dim 3

julia> set_user_solutions!(algo, X0, f);

julia> optimize(f, [0 0 0; 1 1 1.0], algo)
+=========== RESULT ==========+
  iteration: 413
    minimum: 0
  minimizer: [0.0, 0.0, 0.0]
    f calls: 25132
 total time: 0.0856 s
stop reason: Small difference of objective function values.
+============================+
```
