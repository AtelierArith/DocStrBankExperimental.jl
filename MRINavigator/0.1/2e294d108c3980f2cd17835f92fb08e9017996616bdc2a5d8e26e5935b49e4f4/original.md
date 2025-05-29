ReconstructMap(path_ref::String)

Reconstruct the coil sensitivity map using the MRIReco.jl function.

# Arguments

  * `path_rep::String` - path of reference data in ISMRMRD format
  * `thresh::Float64` - masking threshold: increase for reduced mask size, decrease for extended mask size

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 ISMRMRD reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089
