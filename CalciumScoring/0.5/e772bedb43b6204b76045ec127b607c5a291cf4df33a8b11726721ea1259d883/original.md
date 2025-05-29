## `score` (VolumeFraction)

```julia
score(vol::AbstractArray, hu_calcium, hu_heart_tissue, alg::VolumeFraction)

score(vol::AbstractArray, hu_calcium, hu_heart_tissue, voxel_size, alg::VolumeFraction)

score(vol::AbstractArray, hu_calcium, hu_heart_tissue, voxel_size, density_calcium, alg::VolumeFraction)

score(vol::AbstractMatrix, hu_calcium, hu_heart_tissue, alg::VolumeFraction)

score(vol::AbstractMatrix, hu_calcium, hu_heart_tissue, voxel_size, alg::VolumeFraction)

score(vol::AbstractMatrix, hu_calcium, hu_heart_tissue, voxel_size, density_calcium, alg::VolumeFraction)
```

Calculate the number of voxels that are calcified, the volume of the calcification, or the mass of the calcification  depending on the provided arguments.

#### Inputs

  * `vol`: An input region of interest containing all potential calcium.
  * `hu_calcium`: The Hounsfield unit associated with a known calcium density.
  * `hu_heart_tissue`: The Hounsfield unit associated with background heart tissue.
  * `voxel_size`: (optional) The size of an individual pixel/voxel.
  * `density_calcium`: (optional) The density of the previously mentioned calcium.
  * `alg::VolumeFraction`: The algorithm to be used for the calculation.

#### Returns

  * When called with `vol`, `hu_calcium`, `hu_heart_tissue`, and `alg`, this function calculates and returns    the number of voxels that are calcified.
  * When called with `vol`, `hu_calcium`, `hu_heart_tissue`, `voxel_size`, and `alg`, this function calculates    and returns the volume of the calcification.
  * When called with `vol`, `hu_calcium`, `hu_heart_tissue`, `voxel_size`, `density_calcium`, and `alg`, this    function calculates and returns the mass of the calcification.

#### References

[Coronary artery calcium mass measurement based on integrated intensity and volume fraction techniques](https://doi.org/10.1101/2023.01.12.23284482)
