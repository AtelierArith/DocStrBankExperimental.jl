```
MOEAD_DE(weights ;
    F = 0.5,
    CR = 1.0,
    λ = Array{Vector{Float64}}[], # ref. points
    η = 20,
    p_m = -1.0,
    T = round(Int, 0.2*length(weights)),
    δ = 0.9,
    n_r = round(Int, 0.02*length(weights)),
    z = zeros(0),
    B = Array{Int}[],
    s1 = 0.01,
    s2 = 20.0,
    information = Information(),
    options = Options())
```

`MOEAD_DE` implements the original version of MOEA/D-DE. It uses the contraint handling method based on the sum of violations (for constrained optimizaton): `g(x, λ, z) = max(λ .* abs.(fx - z)) + sum(max.(0, gx)) + sum(abs.(hx))`

To use MOEAD_DE, the output from the objective function should be a 3-touple `(f::Vector, g::Vector, h::Vector)`, where `f` contains the objective functions, `g` and `h` are the equality and inequality constraints respectively.

A feasible solution is such that `g_i(x) ≤ 0 and h_j(x) = 0`.

Ref. Multiobjective Optimization Problems With Complicated Pareto Sets, MOEA/D and NSGA-II; Hui Li and Qingfu Zhang.

# Example

Assume you want to solve the following optimizaton problem:

Minimize:

`f(x) = (x_1, x_2)`

subject to:

`g(x) = x_1^2 + x_2^2 - 1 ≤ 0`

`x_1, x_2 ∈ [-1, 1]`

A solution can be:

```julia

# Dimension
D = 2

# Objective function
f(x) = ( x, [sum(x.^2) - 1], [0.0] )

# bounds
bounds = [-1 -1;
           1  1.0
        ]

nobjectives = 2
npartitions = 100

# reference points (Das and Dennis's method)
weights = gen_ref_dirs(nobjectives, npartitions)

# define the parameters
moead_de = MOEAD_DE(weights, options=Options(debug=false, iterations = 250))

# optimize
status_moead = optimize(f, bounds, moead_de)

# show results
display(status_moead)
```
