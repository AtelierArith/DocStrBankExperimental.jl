```
CompositeMeasurementModel(model1, model2, ...)
```

A composite measurement model that combines multiple measurement models. This model acts as all component models concatenated. The tuple returned from [`correct!`](@ref) will be

  * `ll`: The sum of the log-likelihood of all component models
  * `e`: The concatenated innovation vector
  * `S`: A vector of the innovation covariance matrices of the component models
  * `Sᵪ`: A vector of the Cholesky factorizations of the innovation covariance matrices of the component models
  * `K`: A vector of the Kalman gains of the component models

If all sensors operate on at the same rate, and all measurement models are of the same type, it's more efficient to use a single measurement model with a vector-valued measurement function.

# Fields:

  * `models`: A tuple of measurement models
