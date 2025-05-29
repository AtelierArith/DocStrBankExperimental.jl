```
simple_estimator(model::Ising, T::Real, Js::AbstractArray)
```

Returns the following observables as `Dict{String, Any}`

# Observables

  * `"Energy"`

      * energy density
  * `"Energy^2"`

      * square of energy density
  * `"Magnetization"`

      * magnetization density
  * `"|Magnetization|"`

      * absolute value of magnetization density
  * `"Magnetization^2"`

      * square of magnetization density
  * `"Magnetization^4"`

      * quadruple of magnetization density
