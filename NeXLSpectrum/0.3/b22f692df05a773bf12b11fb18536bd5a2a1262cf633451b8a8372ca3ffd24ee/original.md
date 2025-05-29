```
readptx(
    fn::AbstractString, 
    scale::EnergyScale, # Energy scale for hyperspectrum
    props::Dict{Symbol,Any},
    nch::Int; # Number of channels in hyperspectrum
    blocksize = 1,  # Size of blocks to sum to create averaged hyperspectrum
    dets=[true,true,true,true], # Which detectors to include
    frames=1:typemax(Int)) # which frames to include in hyperspectrum
readptx(
    fn::AbstractString, 
    scale::EnergyScale, # Energy scale for hyperspectrum
    nch::Int; # Number of channels in hyperspectrum
    blocksize = 1,  # Size of blocks to sum to create averaged hyperspectrum
    dets=[true,true,true,true], # Which detectors to include
    frames=1:typemax(Int)) # which frames to include in hyperspectrum
```

Read a SEMantics .ptx file into a HyperSpectrum.
