## `score` (Agatston)

```julia
score(vol, spacing, alg::Agatston; kV=120, min_size_mm=1)
score(vol, spacing, mass_cal_factor, alg::Agatston; kV=120, min_size_mm=1)
```

Calculate the calcium score via the traditional Agatston scoring technique, as outlined in the  [original paper](10.1016/0735-1097(90)90282-T). Energy (`kV`) specific `threshold`s are determined based on  previous [publications](https://doi.org/10.1093/ehjci/jey019). Also, it converts the Agatston score to a  calcium mass score via the `mass_cal_factor` if provided.

#### Inputs

  * `vol`: input volume containing just the region of interest
  * `spacing`: known pixel/voxel spacing
  * `alg::Agatston`: Agatston scoring algorithm `Agatston()`
  * `mass_cal_factor`: (optional) a factor to calibrate the calculated mass
  * kwargs:

      * `kV=120`: energy of the input CT scan image
      * `min_size=1`: minimum connected component size (see [`label_components`](https://github.com/JuliaImages/Images.jl))

#### Returns

  * `agatston_score`: total Agatston score
  * `volume_score`: total calcium volume via Agatston scoring
  * `abs_mass_score`: (optional) total calcium mass after calibration, returned only when `mass_cal_factor` is provided

#### References

[Quantification of coronary artery calcium using ultrafast computed tomography](https://doi.org/10.1016/0735-1097(90)90282-t)

[Ultra-low-dose coronary artery calcium scoring using novel scoring thresholds for low tube voltage protocols—a pilot study ](https://doi.org/10.1093/ehjci/jey019)
