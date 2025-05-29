```
predict(m::AbstractGEE; type=:linear)
```

Return the fitted values from the fitted model.  If type is :linear returns the linear predictor, if type is :response returns the fitted mean.
