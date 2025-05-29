```
gqi_rec(dwi::MRI, mask::MRI, odf_dirs::ODF=sphere_642, σ::Float32=Float32(1.25))
```

Perform generalized q-space imaging (GQI) reconstruction of DWIs, and return a `GQI` structure.

If you use this method, please cite: Fang-Cheng Yeh, et al. (2010). Generalized q-sampling imaging. IEEE Transactions on Medical Imaging, 29(9), 1626–1635. https://doi.org/10.1109/TMI.2010.2045126

# Arguments

  * `dwi::MRI`: A series of DWIs, stored in an `MRI` structure with valid `.bvec`  and `.bval` fields
  * `mask::MRI`: A brain mask volume, stored in an `MRI` structure
  * `odf_dirs::ODF=sphere_642`: The vertices and faces of the ODF tessellation, stored in an `ODF` structure
  * `σ::Float32=Float32(1.25)`: Diffusion sampling length factor

# Output

In the `GQI` structure:

  * `.odf`: ODF amplitudes on the half sphere
  * `.peak`: Orientation vectors of the 3 peak ODF amplitudes
  * `.qa`: Quantitative anisotropy for each of the 3 peak orientations
