```
sweep_contract(LTN::LabelledTensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
sweep_contract(TN::TensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
```

Returns the contraction of the `TensorNetwork TN`, or the `LabelledTensorNetwork LTN` using the sweepline contraction algorithm of `arXiv:2101.04125`. The MPS is truncated down to a bond dimension of `χ` whenever any bond dimension exceeds `τ`.

By default the network is checked for validity, planarised, and sweep-connected, where necessary. The keyword flags `valid`, `planar`, and `connected` can be used to skip these, or the flag `fast` can be used to skip them all. If these flags are enabled then contraction may fail on poorly formed networks.

To avoid underflow/overflow issues the contraction value of the network is returned as a tuple `(f::Float64, i::Int64)` where `1≦f<2` or `f` is `0`, representing a value of `f*2^i`. The function `ldexp` can be used to convert this back to a Float64.

`sweep_contract` is non-mutating and acts upon a deep copy of the network, where possible use the more efficient mutating version `sweep_contract!`.
