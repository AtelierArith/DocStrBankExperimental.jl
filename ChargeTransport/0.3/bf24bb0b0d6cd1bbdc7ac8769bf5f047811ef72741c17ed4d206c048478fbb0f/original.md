```julia
mutable struct System
```

A struct holding all information necessary for a drift-diffusion type system.

  * `data::ChargeTransport.Data`: A struct holding all data information, see Data

  * `fvmsys::VoronoiFVM.AbstractSystem`: A struct holding system information for the finite volume system.
