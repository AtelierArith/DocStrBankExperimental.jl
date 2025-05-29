```
LinRegBuilder(p)
```

Create an object from which any variable can be regressed on any other set of variables, optionally with element-wise ridge regularization.  The main function to use with `LinRegBuilder` is `coef`:

```
coef(o::LinRegBuilder, λ = 0; y=1, x=[2,3,...], bias=true, verbose=false)
```

Return the coefficients of a regressing column `y` on columns `x` with ridge (`abs2` penalty) parameter `λ`.  An intercept (`bias`) term is added by default.

# Examples

```
x = randn(1000, 10)
o = fit!(LinRegBuilder(), eachrow(x))

coef(o; y=3, verbose=true)

coef(o; y=7, x=[2,5,4])
```
