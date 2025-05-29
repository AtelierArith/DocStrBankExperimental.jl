```
SelectEcho!(acqd, idx_echo)
```

Extract one or more echoes from the acquisition data structure

# Arguments

  * `acqd::AcquisitionData` - acquisition data structure obtained converting raw data with MRIReco.jl
  * `idx_echo::Vector{Int64}` - vector containing the indexes of the echoes to be selected (starting from 0)

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
