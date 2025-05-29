```
ReconstructSaveMap(path_nifti::String, path_ref::String, thresh::Float64)
```

Reconstruct the coil sensitivity map using the MRIReco.jl function and save it in nifti format without spatial information.

# Arguments

  * `path_nifti::String` - path of the nifti file. The file must have .nii extension
  * `path_rep::String` - path of reference data in ISMRMRD format
  * `thresh::Float64` - masking threshold: increase for reduced mask size, decrease for extended mask size

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792 ISMRMRD reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.26089
