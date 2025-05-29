```
get_pad_transform(gate_data::GateData; probabilities::Bool = false)
```

Returns a transform matrix that pads gate eigenvalues, or gate error probabilities if `probabilities` is `true`, with identity eigenvaleus or error probabilities respectively, up to a constant given by [`get_pad_mask`](@ref), calculated using the gate data `gate_data`.
