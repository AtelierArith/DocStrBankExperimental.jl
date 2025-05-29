```
get_drivers(model::AbstractModel)
```

Returns the `driver` objects for the model - atmospheric and radiative forcing, etc - as a tuple (atmos, radiation, ...). If no drivers are needed by a model, an empty tuple should be returned
