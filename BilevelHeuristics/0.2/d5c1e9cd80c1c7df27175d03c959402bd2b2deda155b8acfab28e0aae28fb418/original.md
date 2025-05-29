```
SABO(;N, K, η_max, δ1, δ2, ε1, ε2, λ, t_reevaluate)
```

Surrogate Algorithm for Bilevel Optimization.

## Parameters

  * `N` Upper level population size
  * `K` Num. of solutions to generate centers.
  * `η_max` Step size
  * `δ1`, `δ2`, `ε1` `ε2` Parameters for conditions to avoid pseudo-feasible solutions.
  * `λ` Parameter for the surrogate model.
  * `t_reevaluate` Indicates how many iterations is reevaluated the lower level.

## Usage

Upper level problem: `F(x,y)` with `x` as the upper-level vector.

```julia-repl
julia> F(x, y) = sum(x.^2) + sum(y.^2)
F (generic function with 1 method)

julia> bounds_ul = [-ones(5) ones(5)];

```

Lower level problem: `f(x, y)` with `y` as the lower-level vector.

```julia-repl
julia> f(x, y) = sum((x - y).^2) + y[1]^2
f (generic function with 1 method)

julia> bounds_ll = [-ones(5) ones(5)];

```

Approximate solution.

```julia-repl
julia> using Metaheuristics

julia> res = optimize(F, f, bounds_ul, bounds_ll, SABO(options_ul=Options(iterations=12)))
+=========== RESULT ==========+
  iteration: 12
    minimum: 
          F: 0.00472028
          f: 0.000641749
  minimizer: 
          x: [-0.03582594991950816, 0.018051141584692676, -0.030154879329873152, -0.017337812299467736, 0.004710839249040477]
          y: [-0.017912974972476316, 0.018051141514328663, -0.030154879385452187, -0.017337812317661405, 0.004710839272021738]
    F calls: 372
    f calls: 513936
    Message: Stopped due completed iterations. 
 total time: 19.0654 s
+============================+

julia> x, y = minimizer(res);

julia> x
5-element Vector{Float64}:
 -0.03582594991950816
  0.018051141584692676
 -0.030154879329873152
 -0.017337812299467736
  0.004710839249040477

julia> y
5-element Vector{Float64}:
 -0.017912974972476316
  0.018051141514328663
 -0.030154879385452187
 -0.017337812317661405
  0.004710839272021738

julia> Fmin, fmin = minimum(res)
(0.004720277765002139, 0.0006417493438175533)
```

## Citation

> Mejía-de-Dios, J. A., & Mezura-Montes, E. (2020, June). A surrogate-assisted metaheuristic for bilevel optimization. In Proceedings of the 2020 Genetic and Evolutionary Computation Conference (pp. 629-635).

