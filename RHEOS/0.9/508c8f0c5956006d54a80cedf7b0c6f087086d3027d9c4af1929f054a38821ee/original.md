```
modulusfunction(data::RheoFreqData, Gp::T1, Gpp::T2) where {T1<:Function, T2<:Function}
modulusfunction(Gp::T1, Gpp::T2, data::RheoFreqData) where {T1<:Function, T2<:Function}
```

Returns a new `RheoFreqData` with a modulus calculated using the functions `Gp` and `Gpp` provided,  applied to freqency values present in the input `data`.

Normally used with a `RheoFreqData` generated using the `frequencyspec` function.
