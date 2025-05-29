```
QBCA(;N, K, η_ul_max, η_ll_max, α, β, autodiff)
```

Quasi-newton BCA uses ECA (upper-level) and BFGS (lower-level).

## Parameters

  * `N` Upper level population size
  * `K` Num. of solutions to generate centers.
  * `η_ul_max` UL step size.
  * `η_ll_max` LL step size.
  * `α, β` Parameters for the Tikhnonov regularization.
  * `autodiff=:finite` Used to approximate LL derivates.

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
julia> res = optimize(F, f, bounds_ul, bounds_ll, QBCA())
+=========== RESULT ==========+
  iteration: 71
    minimum: 
          F: 1.20277e-06
          f: 1.8618e-08
  minimizer: 
          x: [-0.00019296602928680934, -0.00031720504506331244, 0.00047217689470620765, 0.00014459596611862214, 0.00048345619641040644]
          y: [-9.647494056567316e-5, -0.0003171519406858993, 0.00047209784939209284, 0.00014457176048263256, 0.0004833752613377002]
    F calls: 2130
    f calls: 366743
    Message: Stopped due UL small fitness variance. 
 total time: 7.7909 s
+============================+

julia> x, y = minimizer(res);

julia> x
5-element Vector{Float64}:
 -0.00019296602928680934
 -0.00031720504506331244
  0.00047217689470620765
  0.00014459596611862214
  0.00048345619641040644

julia> y
5-element Vector{Float64}:
 -9.647494056567316e-5
 -0.0003171519406858993
  0.00047209784939209284
  0.00014457176048263256
  0.0004833752613377002

julia> Fmin, fmin = minimum(res)
(1.2027656204730873e-6, 1.8617960564375732e-8)
```

## Citation

> Mejía-de-Dios, J. A., & Mezura-Montes, E. (2019, June). A metaheuristic for bilevel optimization using tykhonov regularization and the quasi-newton method. In 2019 IEEE Congress on Evolutionary Computation (CEC) (pp. 3134-3141). IEEE.

