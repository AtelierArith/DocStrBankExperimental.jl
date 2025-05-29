```julia
struct UAIModel{ET, FT<:(TensorInference.Factor{ET})}
```

### Fields

  * `nvars` is the number of variables,
  * `cards` is a vector of cardinalities for variables,
  * `factors` is a vector of factors,
