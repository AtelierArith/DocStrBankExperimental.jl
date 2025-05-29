```
struct NuisanceCorrelation
```

Fields:  

  * `unc_key::Symbol`: Name of uncertainty category.
  * `meas1::Symbol`: Name of first measurement.
  * `meas2::Symbol`: Name of second measurement.
  * `prior::Distribution`: Prior distribution. Accepts the type `Distribution` and all other                types accepted by BAT.NamedTupleDist, e.g. `Interval` or `Real`.

Constructors:  

```julia
NuisanceCorrelation(unc_key::Symbol, meas1::Symbol, meas2::Symbol, prior::Any)
```
