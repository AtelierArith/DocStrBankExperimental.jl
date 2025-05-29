```
fit(Hurdle,M,f,df; fpos=Xpos, <keyword arguments>)
```

Takes dataframe and two formulas, one for each model part. Otherwise same arguments as [`fit(::Hurdle)`](@ref)

# Example

```julia
  fit(Hurdle,GeneralizedLinearModel,@formula(y ~ x1*x2), df; fpos=@formula(y ~ x1*x2+x3))
```
