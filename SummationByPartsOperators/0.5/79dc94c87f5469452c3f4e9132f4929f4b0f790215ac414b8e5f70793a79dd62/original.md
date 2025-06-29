```
function_space_operator(basis_functions, nodes, source;
                        derivative_order = 1, accuracy_order = 0,
                        opt_alg = Optim.LBFGS(), options = Optim.Options(g_tol = 1e-14, iterations = 10000),
                        verbose = false)
```

Construct an operator that represents a first-derivative operator in a function space spanned by the `basis_functions`, which is an iterable of functions. The operator is constructed on the interval `[x_min, x_max]` with the nodes `nodes`, where `x_min` is taken as the minimal value in `nodes` and `x_max` the maximal value. Note that the `nodes` will be sorted internally. The `accuracy_order` is the order of the accuracy of the operator, which can optionally be passed, but does not have any effect on the operator. The operator is constructed solving an optimization problem with Optim.jl. You can specify the optimization algorithm and options for the optimization problem with the keyword arguments `opt_alg` and `options` respectively, see also the [documentation of Optim.jl](https://julianlsolvers.github.io/Optim.jl/stable/user/config/)

The operator that is returned follows the general interface. Currently, it is wrapped in a [`MatrixDerivativeOperator`](@ref), but this might change in the future. In order to use this function, the package `Optim` must be loaded.

See also [`GlaubitzNordströmÖffner2023`](@ref).

!!! compat "Julia 1.9"
    This function requires at least Julia 1.9.


!!! warning "Experimental implementation"
    This is an experimental feature and may change in future releases.

