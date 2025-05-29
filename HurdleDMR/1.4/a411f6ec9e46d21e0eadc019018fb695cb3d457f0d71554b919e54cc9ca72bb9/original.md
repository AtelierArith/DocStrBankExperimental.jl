```
coef(m::Hurdle; select=MinAICc())
```

Returns a selected segment of the coefficient matrices of the fitted the TwoPartModel.

# Example:

```julia
  m = fit(Hurdle,GeneralizedLinearModel,X,y; Xpos=Xpos)
  coefspos, coefszero = coef(m)
```

# Keywords

  * `kwargs...` are passed along to two coef() calls on the two model parts.
