```
get_wht_transform(gate_data::GateData; inverse::Bool = false)
```

Returns a transform matrix that maps padded gate error probabilities to padded gate eigenvalues, or the inverse transform if `inverse` is `true`, calculated using the gate data `gate_data`.
