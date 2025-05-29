```
niftiSaveImg(img::AbstractArray{T}, acq::AcquisitionData, path_nifti::String)
```

Save the module of the reconstruction output in nifti format, without spatial information.

# Arguments

  * `img::AbstractArray{T}` - reconstruction output
  * `acq::AcquisitionData` - reconstruction input (MRIReco.jl) needed for saving the voxel dimension
  * `path_nifti::String` - path of the nifti file. The file must have .nii extension

MRIReco reference: https://onlinelibrary.wiley.com/doi/epdf/10.1002/mrm.28792
