```
sweep_contract_dangling(LTN::LabelledTensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
sweep_contract_dangling(TN::TensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
```

A modified version of `sweep_contract` which can be used to evaluate open tensor networks which possess dangling legs. This is done by halting the sweep procedure before the final tensor is contracted and returning the MPS approximating the network so far. To do this a dummy tensor must be present in the network which is above the rest of the network, i.e. has a higher y coordinate.

Similar to sweep_contract underflow/overflow issues are avoided by return the MPS in a floating point format. The output is returned as a tuple `(mps::MPS, i::Int64)` where `mps` has a 2-norm in [1,2), representing the MPS `mps*2^i`.

For other details see the documentation of `sweep_contract`.
