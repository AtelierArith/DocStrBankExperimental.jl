```
SMS_EMOA(;
    N = 100,
    η_cr = 20,
    p_cr = 0.9,
    η_m = 20,
    p_m = 1.0 / D,
    n_samples = 10_000,
    information = Information(),
    options = Options(),
)
```

Parameters for the metaheuristic SMS-EMOA.

Parameters:

  * `N` Population size.
  * `η_cr`  η for the crossover.
  * `p_cr` Crossover probability.
  * `η_m`  η for the mutation operator.
  * `p_m` Mutation probability (1/D for D-dimensional problem by default).
  * `n_samples` number of samples to approximate hypervolume in many-objective (M > 2).

To use SMS_EMOA, the output from the objective function should be a 3-touple `(f::Vector, g::Vector, h::Vector)`, where `f` contains the objective functions, `g` and `h` are inequality, equality constraints respectively.

A feasible solution is such that `g_i(x) ≤ 0 and h_j(x) = 0`.

```julia
using Metaheuristics

# Dimension
D = 2

# Objective function
f(x) = ( x, [sum(x.^2) - 1], [0.0] ) 

# bounds
bounds = [-1 -1;
           1  1.0
        ]

# define the parameters (use `SMS_EMOA()` for using default parameters)
sms_emoa = SMS_EMOA(N = 100, p_cr = 0.85)

# optimize
status = optimize(f, bounds, sms_emoa)

# show results
display(status)
```
