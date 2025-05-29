```
NSGA2(;
    N = 100,
    η_cr = 20,
    p_cr = 0.9,
    η_m = 20,
    p_m = 1.0 / D,
    information = Information(),
    options = Options(),
)
```

Parameters for the metaheuristic NSGA-II.

Parameters:

  * `N` Population size.
  * `η_cr`  η for the crossover.
  * `p_cr` Crossover probability.
  * `η_m`  η for the mutation operator.
  * `p_m` Mutation probability (1/D for D-dimensional problem by default).

To use NSGA2, the output from the objective function should be a 3-touple `(f::Vector, g::Vector, h::Vector)`, where `f` contains the objective functions, `g` and `h` are inequality, equality constraints respectively.

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

# define the parameters (use `NSGA2()` for using default parameters)
nsga2 = NSGA2(N = 100, p_cr = 0.85)

# optimize
status = optimize(f, bounds, nsga2)

# show results
display(status)
```
