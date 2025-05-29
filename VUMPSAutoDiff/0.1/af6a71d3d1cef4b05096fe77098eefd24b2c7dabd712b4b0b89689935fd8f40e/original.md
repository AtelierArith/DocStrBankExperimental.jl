```
AbstractLinearMap
```

Abstract type representing linear maps used in transfer matrix calculations.  Subtypes should implement these required methods:

1. **Vector space definitions**:

      * `right_space(TM)`: Returns the vector space for right environment calculations
      * `left_space(TM)`: Returns the vector space for left environment calculations
2. **Transfer operations**:

      * `left_transfer(TM, v)`: Apply transfer matrix to left environment vector `v`
      * `right_transfer(TM, v)`: Apply transfer matrix to right environment vector `v`
3. **Automatic differentiation**:

      * `ChainRulesCore.rrule` constructor: Defines gradient propagation rules

Concrete implementations can be seen in:

  * `MPSMPSTransferMatrix` (MPS-MPS systems)
  * `MPSMPOMPSTransferMatrix` (MPS-MPO-MPS systems)
  * `ACMap` (the linear map for AC in VUMPS iteration)

Subtypes must implement the core transfer operations to enable both forward  calculations and backward gradient propagation through environment tensors.
