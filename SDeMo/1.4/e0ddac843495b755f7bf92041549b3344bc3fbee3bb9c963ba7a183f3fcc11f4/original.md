```
vif(::AbstractSDM, tr=:)
```

Returns the VIF for the variables used in a SDM, optionally restricting to some training instances (defaults to `:` for all points). The VIF is calculated on the de-meaned predictors.
