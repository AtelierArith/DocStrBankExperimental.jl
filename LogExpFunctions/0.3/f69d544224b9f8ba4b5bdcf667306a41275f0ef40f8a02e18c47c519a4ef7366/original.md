```julia
softplus(x)

```

The generalized `softplus` function (Wiemann et al., 2024) takes an additional optional parameter `a` that control  the approximation error with respect to the linear spline. It defaults to `a=1.0`, in which case the softplus is  equivalent to [`log1pexp`](@ref).

See:

  * Wiemann, P. F., Kneib, T., & Hambuckers, J. (2024). Using the softplus function to construct alternative link functions in generalized linear models and beyond. Statistical Papers, 65(5), 3155-3180.
