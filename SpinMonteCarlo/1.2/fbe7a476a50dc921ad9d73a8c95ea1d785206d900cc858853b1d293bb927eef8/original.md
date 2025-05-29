```
improved_estimator(model::Potts, T::Real, Js::AbstractArray, sw::SWInfo)
```

Returns the following observables as `Dict{String, Any}` using cluster information `sw`

# Observables

  * `"Energy"`

      * energy density
  * `"Energy^2"`

      * square of energy density
  * `"Magnetization"`

      * magnetization density
  * `"|Magnetization|"`

      * absolute value of magnetization density
  * `"|Magnetization|^2"`

      * square of magnetization density
  * `"|Magnetization|^4"`

      * quadruple of magnetization density
  * `"Clustersize^2"`

      * $\sum_c r_c^2$, where $r_c$ is the size density of $c$-th cluster
  * `"Clustersize^4"`

      * $\sum_c r_c^4$
  * `"Clustersize^2 Clustersize^2"`

      * $\sum_{c\ne c'} r_c^2 r_{c'}^2$
