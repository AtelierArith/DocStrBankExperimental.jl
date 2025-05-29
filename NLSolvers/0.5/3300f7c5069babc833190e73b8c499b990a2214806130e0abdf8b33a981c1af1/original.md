# Adam

## Constructor

```julia
    Adam(; alpha=0.0001, beta_mean=0.9, beta_var=0.999, epsilon=1e-8)
```

## Description

Adam is a gradient based optimizer that choses its search direction by building up estimates of the first two moments of the gradient vector. This makes it suitable for problems with a stochastic objective and thus gradient. The method is introduced in [1] where the related AdaMax method is also introduced, see `?AdaMax` for more information on that method.

## References

[1] https://arxiv.org/abs/1412.6980
