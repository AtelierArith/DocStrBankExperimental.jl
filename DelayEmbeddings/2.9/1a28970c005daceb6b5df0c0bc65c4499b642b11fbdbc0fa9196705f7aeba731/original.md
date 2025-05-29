```
stochastic_indicator(s::AbstractVector, τ:Int, ds = 2:5) -> E₂s
```

Compute an estimator for apparent randomness in a delay embedding with `ds` dimensions.

## Description

Given the scalar timeseries `s` and the embedding delay `τ` compute the values of `E₂` for each `d ∈ ds`, according to Cao's Method (eq. 5 of [^Cao1997]).

Use this function to confirm that the input signal is not random and validate the results of [`delay_afnn`](@ref). In the case of random signals, it should be `E₂ ≈ 1 ∀ d`.
