# Adam

## Constant `alpha` case (default) constructor:

```julia
    Adam(; alpha=0.0001, beta_mean=0.9, beta_var=0.999, epsilon=1e-8)
```

## Scheduled `alpha` case constructor:

Alternative to the above (default) usage where `alpha` is a fixed constant for all the iterations, the following constructor provides flexibility for `alpha` to be a callable object (a scheduler) that maps the current iteration count to a value of `alpha` that is to-be used for the current optimization iteraion's update step. This helps us in scheduling `alpha` over the iterations as desired, using the following usage,

```julia
    # Let alpha_scheduler be iteration -> alpha value mapping callable object
    Adam(; alpha=alpha_scheduler, other_kwargs...)
```

## Description

Adam is a gradient based optimizer that choses its search direction by building up estimates of the first two moments of the gradient vector. This makes it suitable for problems with a stochastic objective and thus gradient. The method is introduced in [1] where the related AdaMax method is also introduced, see `?AdaMax` for more information on that method.

## References

[1] https://arxiv.org/abs/1412.6980
