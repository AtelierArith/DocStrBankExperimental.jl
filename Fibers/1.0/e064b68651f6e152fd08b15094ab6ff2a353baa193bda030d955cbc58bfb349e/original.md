```
dsi_rec(dwi::MRI, mask::MRI, odf_dirs::ODF=sphere_642, σ::Float32=Float32(1.25))
```

Perform diffusion spectrum imaging (DSI) reconstruction of DWIs, and return a `DSI` structure.

If you use this method, please cite: Wedeen, V. J., et al. (2005). Mapping complex tissue architecture with diffusion spectrum magnetic resonance imaging. Magnetic resonance in medicine, 54(6), 1377–1386. https://doi.org/10.1002/mrm.20642

# Arguments

  * `dwi::MRI`: A series of DWIs, stored in an `MRI` structure with valid `.bvec`  and `.bval` fields
  * `mask::MRI`: A brain mask volume, stored in an `MRI` structure
  * `odf_dirs::ODF=sphere_642`: The vertices and faces of the ODF tessellation, stored in an `ODF` structure
  * `hann_width::Int=32`: Width of Hanning window (in q-space voxels)

# Output

In the `DSI` structure:

  * `.pdf`: PDF amplitudes on the half sphere
  * `.odf`: ODF amplitudes on the half sphere
  * `.peak`: Orientation vectors of the 3 peak ODF amplitudes
  * `.qa`: Quantitative anisotropy for each of the 3 peak orientations
