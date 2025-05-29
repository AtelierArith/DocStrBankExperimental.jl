```julia
struct RayBasis3D{T1, T2, T3<:(AbstractVector), T4, T5} <: DataDrivenAcoustics.DataDrivenPropagationModel{T1}
```

A 3D spherical wave RBNN formualtion.

  * `env`: data driven underwater environment
  * `calculatefield`: function to estimate acoustic field (default: `RayBasis3DCal`)
  * `nrays`: number of rays (default: 60)
  * `θ`: nominal azimuthal angle of arrival rays in radian (default: missing)
  * `ψ`: nominal elevation angle of arrival rays in radian (default: missing)
  * `d`: nominal propagation distance of arrival rays  in meters (default: missing)
  * `eθ`: error to nominal azimuthal angle of arrival rays in radian (default: missing)
  * `eψ`: error to nominal elevation angle of arrival rays in radian (default: missing)
  * `ed`: error to nominal propagation distance of arrival rays in meters (default: missing)
  * `A`: amplitude of arrival rays (default: missing)
  * `ϕ`: phase of a rays in radian (default: missing)
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
