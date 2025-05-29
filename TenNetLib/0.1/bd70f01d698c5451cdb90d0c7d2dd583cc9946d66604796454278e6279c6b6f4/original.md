```
mutable struct SweepData
    sweepcount::Int
    maxchi::Vector{Int}
    energy::Vector{Float64}
    entropy::Vector{Float64}
    maxtruncerr::Vector{Float64}
    lasteigs::Vector{Vector{Float64}}
end
```

Holds historical data after each (full)sweep. Requires for convergence check etc.

  * `sweepcount::Int`: Number of fullsweeps performed.
  * `maxchi::Vector{Int}`: Maximum MPS bond/link dimensions after every sweep.
  * `energy::Vector{Float64}`: Energies after every sweep.
  * `entropy::Vector{Float64}`: Mid-chain entropies after every sweep.
  * `maxtrucerr::Vector{Float64}`: Maximum truncation error after every sweep.
  * `lasteigs::Vector{Vector{Float64}}`: Spectrum of eigenvalues at each bond after previous halfsweep.

#### Default constructor:

  * `SweepData()`: Initialize an empty `SweepData` object.
