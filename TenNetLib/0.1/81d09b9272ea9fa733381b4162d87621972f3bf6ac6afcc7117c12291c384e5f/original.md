```
mutable struct TDVPEngine{T <: Union{ProjMPO,
                                     ProjMPOSum2,
                                     ProjMPO_MPS2,
                                     ProjMPOSum_MPS,
                                     ProjCouplingModel,
                                     ProjCouplingModel_MPS}}
```

Holds the `MPS` state, `SweepData`, and absolute elpased time for TDVP simulations.

  * `sysenv::StateEnvs`: Holds the state psi and environments PH.
  * `swdata::SweepData`: Holds the historical data after each (full)sweep.
  * `abstime::Float64`: Absolute elapsed time.
