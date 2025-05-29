```
bat_compare(
    samples_1::DensitySampleVector,
    samples_2::DensitySampleVector;
    nsamples::Symbol=:effective
)
```

Compares two `DensitySampleVector`s given by `samples_1` and `samples_2` applying the Kolmogorov-Smirnov test for all marginals.

`nsamples` specifies how to define a number of samples in the Kolmogorov-Smirnov distribution. The default value is `nsamples=:effective`, which uses the effective number of samples estimated by `bat_eff_sample_size`. The optimal keywords:

  * `:length`  — length of the `DensitySamplesVector` is used
  * `:weights` — the sum of the weights is used

Returns a NamedTuple of the shape

```julia
(result = X::TypedTables.Table, ...)
```
