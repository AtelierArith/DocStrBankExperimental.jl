```
RheoFreqData(Gp::Vector{T1}, Gpp::Vector{T2}, ω::Vector{T3}, log::OrderedDict{Any,Any}) where {T1<:Real, T2<:Real, T3<:Real}
```

`RheoFreqData` contains storage modulus, loss modulus and frequency data.

If preferred, an instance can be generated manually by just providing the three data vectors in the right order.

# Fields

  * `Gp`: storage modulus
  * `Gpp`: loss modulus
  * `ω`: frequency
  * `log`: a log of struct's events, e.g. preprocessing
