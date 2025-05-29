```
get_x(xyz::XYZ, ind = trues(xyz.traj.N),
      features_setup::Vector{Symbol}   = [:mag_1_uc,:TL_A_flux_a];
      features_no_norm::Vector{Symbol} = Symbol[],
      terms             = [:permanent,:induced,:eddy],
      sub_diurnal::Bool = false,
      sub_igrf::Bool    = false,
      bpf_mag::Bool     = false)
```

Get `x` data matrix.

**Arguments:**

  * `xyz`:              `XYZ` flight data struct
  * `ind`:              selected data indices
  * `features_setup`:   vector of features to include
  * `features_no_norm`: (optional) vector of features to not normalize
  * `terms`:            (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `sub_diurnal`:      (optional) if true, subtract diurnal from scalar magnetometer measurements
  * `sub_igrf`:         (optional) if true, subtract IGRF from scalar magnetometer measurements
  * `bpf_mag`:          (optional) if true, bpf scalar magnetometer measurements

**Returns:**

  * `x`:        `N` x `Nf` data matrix (`Nf` is number of features)
  * `no_norm`:  length-`Nf` Boolean indices of features to not be normalized
  * `features`: length-`Nf` feature vector (including components of TL `A`, etc.)
  * `l_segs`:   length-`N_lines` vector of lengths of `lines`, sum(l_segs) = `N`
