```
mutable struct SweepDataTTN
    sweepcount::Int
    maxchi::Vector{Int}
    energy::Vector{Float64}
end
```

Holds historical data after each (full)sweep of the TTN. Requires for convergence check etc.

  * `sweepcount::Int`: Number of fullsweeps performed.
  * `maxchi::Vector{Int}`: Maximum MPS bond/link dimensions after every sweep.
  * `energy::Vector{Float64}`: Energies after every sweep.

#### Default constructor:

  * `SweepDataTTN()`: Initialize an empty `SweepData` object.
