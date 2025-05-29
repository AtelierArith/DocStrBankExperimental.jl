```
position!(P::ProjMPO, psi::MPS, pos::Int)
```

Given an MPS `psi`, shift the projection of the MPO represented by the ProjMPO `P` such that the set of unprojected sites begins with site `pos`. This operation efficiently reuses previous projections of the MPO on sites that have already been projected. The MPS `psi` must have compatible bond indices with the previous projected MPO tensors for this operation to succeed.
