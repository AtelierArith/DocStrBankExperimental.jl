```
QBCA2(;N, K, η_max, δ1, δ2, ε1, ε2, λ, t_reevaluate)
```

Quasi-newton BCA uses ECA (upper-level) and BFGS (lower-level).

## Parameters

  * `N` Upper level population size
  * `K` Num. of solutions to generate centers.
  * `η_max` Step size
  * `δ1`, `δ2`, `ε1` `ε2` Parameters for conditions to avoid pseudo-feasible solutions.

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
julia> res = optimize(F, f, bounds_ul, bounds_ll, QBCA2())
+=========== RESULT ==========+
  iteration: 59
    minimum: 
          F: 3.95536e-07
          f: 9.2123e-11
  minimizer: 
          x: [-1.3573722472608445e-5, -0.00012074600446520904, -0.00035025471067487137, -0.0002315301345354928, -8.239473503719106e-5]
          y: [-6.786860530140986e-6, -0.00012074599672993571, -0.00035025467380887673, -0.00023153010993486042, -8.239472729799499e-5]
    F calls: 1775
    f calls: 299157
    Message: Stopped due UL small fitness variance. 
 total time: 5.6968 s
+============================+

julia> x, y = minimizer(res);

julia> x
5-element Vector{Float64}:
 -1.3573722472608445e-5
 -0.00012074600446520904
 -0.00035025471067487137
 -0.0002315301345354928
 -8.239473503719106e-5

julia> y
5-element Vector{Float64}:
 -6.786860530140986e-6
 -0.00012074599672993571
 -0.00035025467380887673
 -0.00023153010993486042
 -8.239472729799499e-5

julia> Fmin, fmin = minimum(res)
(3.9553637806596925e-7, 9.212297088378278e-11)
```

## Citation

> Mejía-de-Dios, J. A., Mezura-Montes, E., & Toledo-Hernández, P. (2022). Pseudo-feasible solutions in evolutionary bilevel optimization: Test problems and performance assessment. Applied Mathematics and Computation, 412, 126577.

