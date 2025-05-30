```
makehomogeneous(mag::NIVolume; sigma_mm=7, nbox=15)
```

Homogeneity correction for NIVolume from NIfTI files.

### Keyword arguments:

  * `sigma_mm`: sigma size for smoothing to obtain bias field. Takes NIfTI voxel size into account
  * `nbox`: Number of boxes in each dimension for the box-segmentation step.
