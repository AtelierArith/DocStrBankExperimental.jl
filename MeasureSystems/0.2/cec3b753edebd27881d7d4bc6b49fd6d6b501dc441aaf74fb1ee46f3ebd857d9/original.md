```
@unitdim(U::UnitSystem,S::UnitSystem) -> dimtext(::typeof(normal(U))) = dimtext(normal(S))
```

Specify the `print` output for each base dimension of `U` upon prior existing `S` data.

```Julia
@unitdim EMU Gauss
@unitdim ESU Gauss
@unitdim LorentzHeaviside Gauss
@unitdim SI2019 Metric
@unitdim SI1976 Metric
@unitdim CODATA Metric
@unitdim Conventional Metric
@unitdim International Metric
@unitdim InternationalMean Metric
@unitdim Survey English
```

These standard examples are some of the built-in defaults.
