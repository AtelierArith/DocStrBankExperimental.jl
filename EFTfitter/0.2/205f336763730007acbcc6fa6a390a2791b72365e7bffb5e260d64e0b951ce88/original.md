```
Prediction(pred::Float64, unc::Float64)
```

Represents the prediction, i.e. the nominal value and the associated absolute uncertainty, of an observable for a given set of parameters.

# Fields

  * `pred::Float64`: The prediction value.
  * `unc::Float64`: The absolute uncertainty associated with the prediction.

# Constructors

  * `Prediction(a::Float64)`: Constructs a `Prediction` with a given value `a` and an uncertainty of `0.0`.
  * `Prediction(a::Tuple{Float64, Float64})`: Constructs a `Prediction` from a tuple where the first element is the prediction value and the second is the uncertainty.
  * `Prediction(a::Prediction)`: Identity constructor, returns the input `Prediction` object.
