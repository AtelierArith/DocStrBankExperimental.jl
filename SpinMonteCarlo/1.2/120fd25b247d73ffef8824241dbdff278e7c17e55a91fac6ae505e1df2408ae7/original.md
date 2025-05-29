```
simple_estimator(model::AshkinTeller, T::Real, Jsigma, Jtau, K)
```

Returns the following observables as `Dict{String, Any}`

# Observables

  * `"Energy"`

      * energy density
  * `"Energy^2"`

      * square of energy density
  * `"|Magnetization|"`

      * absolute value of magnetization density, $|m| = \sqrt{ (\sum_i \sigma_i )^2 + (\sum_i \tau_i)^2 } / N$
  * `"|Magnetization|^2"`

      * square of magnetization density
  * `"|Magnetization|^4"`

      * quadruple of magnetization density
  * `"Magnetization sigma"`

      * magnetization density (sigma spin)
  * `"|Magnetization sigma|"`
  * `"Magnetization sigma^2"`
  * `"Magnetization sigma^4"`
  * `"Magnetization tau"`

      * magnetization density (tau spin)
  * `"|Magnetization tau|"`
  * `"Magnetization tau^2"`
  * `"Magnetization tau^4"`
