```
AnelasticAttenuationParameters
```

Struct for anelastic attenuation parameters. Holds fields:

  * `Q0` quality factor at 1 Hz
  * `η` quality exponent ∈ [0,1)
  * `cQ` velocity (km/s) along propagation path used to determine `Q(f)`
  * `rmetric` is a symbol `:Rrup` or `:Rps` to define which distance metric is used for anelastic attenuation
