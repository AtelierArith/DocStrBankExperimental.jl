```julia
struct RayBasis2DCurv{T1, T2, T3<:(AbstractVector), T4, T5} <: DataDrivenAcoustics.DataDrivenPropagationModel{T1}
```

A 2D plane wave RBNN formualtion by modeling curvature of wavefornt.

  * `env`: data driven underwater environment
  * `calculatefield`: function to estimate acoustic field (default: `RayBasis2DCurvCal`)
  * `nrays`: number of rays (default: 60)
  * `θ`: azimuthal angle of arrival ray in radian (default: missing)
  * `A`: amplitude of arrival rays (default: missing)
  * `ϕ`: phase of a rays in radian (default: missing)
  * `d`: distance in meters to help in modeling curvature of wavefornt (default: missing)
  * `k`: angular wavenumber in rad/m (default: missing)
  * `trainable`: trainable parameters (default: empty)
  * `ini_lr`: initial learning rate (default: 0.001)
  * `trainloss`: loss function used in training and model update (default: `rmseloss`)
  * `dataloss`: data loss function to calculate benchmarking validation error for early stopping (default: `rmseloss`)
  * `ratioₜ`: data split ratio = number of training data/(number of training data + number of validation data) (default: 0.7)
  * set `seed` to `true` to seed random data selection order (default: `false`)
  * `maxepoch`: maximum number of training epoches allowed (default: 10000000)
  * `ncount`: maximum number of tries before reducing learning rate (default: 5000)
  * model training ends once learning rate is smaller than `minlearnrate` (default: 1e-6)
  * learning rate is reduced by `reducedlearnrate` once `ncount` is reached (default: 10)
  * set `showloss` to true to display training and validation errors during the model training process, if the validation error is historically the best. (default: `false`)
