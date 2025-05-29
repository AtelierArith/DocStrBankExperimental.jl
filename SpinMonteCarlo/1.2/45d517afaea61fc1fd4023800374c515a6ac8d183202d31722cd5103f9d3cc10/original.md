```
simple_estimator(model::Clock, T::Real, Js::AbstractArray)
simple_estimator(model::XY, T::Real, Js::AbstractArray)
```

Returns the following observables as `Dict{String, Any}`

# Observables

  * `"Energy"`

      * Energy per spin (site)
  * `"Energy^2"`
  * `"|Magnetization|"`

      * Absolute value of total magnetization per spin (order paremeter)
  * `"|Magnetization|^2"`
  * `"|Magnetization|^4"`
  * `"Magnetization x"`

      * x component of total magnetization per spin (order paremeter)
  * `"|Magnetization x|"`
  * `"Magnetization x^2"`
  * `"Magnetization x^4"`
  * `"Magnetization y"`

      * y component of total magnetization per spin (order paremeter)
  * `"|Magnetization y|"`
  * `"Magnetization y^2"`
  * `"Magnetization y^4"`
  * `"Helicity Modulus x"`
  * `"Helicity Modulus y"`
