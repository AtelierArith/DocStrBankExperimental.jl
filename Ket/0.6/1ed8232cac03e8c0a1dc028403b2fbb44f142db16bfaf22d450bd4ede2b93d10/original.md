```
tensor_probability(rho::Hermitian, all_Aax::Vector{Measurement}...)
tensor_probability(rho::Hermitian, Aax::Vector{Measurement}, N::Integer)
```

Applies N sets of measurements onto a state `rho` to form a probability array. If all parties apply the same measurements, use the shorthand notation.
