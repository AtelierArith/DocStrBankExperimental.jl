# NelderMead

## Constructor

```julia
NelderMead(; parameters = nmparameters,
             initial_simplex = AffineSimplex())
```

The constructor takes 2 keywords:

  * `parameters`, an instance of either `AdaptiveParameters` or `FixedParameters`,

and is used to generate parameters for the Nelder-Mead Algorithm

  * `initial_simplex`, an instance of `AffineSimplexer`

## Description

Our current implementation of the Nelder-Mead algorithm is based on [1] and [3]. Gradient-free methods can be a bit sensitive to starting values and tuning parameters, so it is a good idea to be careful with the defaults provided in Optim.jl.

Instead of using gradient information, Nelder-Mead is a direct search method. It keeps track of the function value at a number of points in the search space. Together, the points form a simplex. Given a simplex, we can perform one of four actions: reflect, expand, contract, or shrink. Basically, the goal is to iteratively replace the worst point with a better point. More information can be found in [1], [2] or [3].

## References

  * [1] Nelder, John A. and R. Mead (1965). "A simplex method for function minimization". Computer Journal 7: 308–313. doi:10.1093/comjnl/7.4.308
  * [2] Lagarias, Jeffrey C., et al. "Convergence properties of the Nelder–Mead simplex method in low dimensions." SIAM Journal on Optimization 9.1 (1998): 112-147
  * [3] Gao, Fuchang and Lixing Han (2010). "Implementing the Nelder-Mead simplex algorithm with adaptive parameters". Computational Optimization and Applications. doi:10.1007/s10589-010-9329-3
