```
improved_estimator(model::QuantumXXZ, T::Real, Js::AbstractArray, uf::UnionFind)
```

Returns the following observables as `Dict{String, Any}` using loop information `uf`

# Observables

  * `"Sign"`

      * Sign of the weight function
  * `"Sign * Energy"`

      * Energy per spin (site)
  * `"Sign * Energy^2"`
  * `"Sign * Magnetization"`

      * Total magnetization (Sz) per spin (site)
  * `"Sign * |Magnetization|"`
  * `"Sign * Magnetization^2"`
  * `"Sign * Magnetization^4"`
