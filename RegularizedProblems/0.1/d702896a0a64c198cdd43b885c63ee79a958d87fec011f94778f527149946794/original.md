```
rmodel = RegularizedNLPModel(model, regularizer)
rmodel = RegularizedNLSModel(model, regularizer)
```

An aggregate type to represent a regularized optimization model, .i.e., of the form

```
minimize f(x) + h(x),
```

where f is smooth (and is usually assumed to have Lipschitz-continuous gradient), and h is lower semi-continuous (and may have to be prox-bounded).

The regularized model is made of

  * `model <: AbstractNLPModel`: the smooth part of the model, for example a `FirstOrderModel`
  * `h`: the nonsmooth part of the model; typically a regularizer defined in `ProximalOperators.jl`
  * `selected`: the subset of variables to which the regularizer h should be applied (default: all).

This aggregate type can be used to call solvers with a single object representing the model, but is especially useful for use with SolverBenchmark.jl, which expects problems to be defined by a single object.
