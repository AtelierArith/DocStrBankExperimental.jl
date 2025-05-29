```
loadRawData(params::Dict{Symbol, Any})
```

Load the raw data file saved in ISMRMRD format in julia using MRIReco.jl Call ExtractNoiseData!, OrderSlices!, ReverseBipolar!, RemoveRef!. Check the specific functions for info.

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 ISMRMRD reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089

# Arguments

  * `params::Dict{Symbol, Any}` - MRINavigator parameter structure, check defaultNavParams() for info
