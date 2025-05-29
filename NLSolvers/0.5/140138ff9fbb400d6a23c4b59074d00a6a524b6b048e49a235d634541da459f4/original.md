```
AdaMax(; alpha=0.002, beta_mean=0.9, beta_var=0.999)
```

# Adam

## Constructor

```julia
    AdaMax(; alpha=0.002, beta_mean=0.9, beta_var=0.999)
```

## Description

AdaMax is a gradient based optimizer that choses its search direction by building up estimates of the first two moments of the gradient vector. This makes it suitable for problems with a stochastic objective and thus gradient. The method is introduced in [1] where the related Adam method is also introduced, see `?Adam` for more information on that method.

[1] https://arxiv.org/abs/1412.6980
