```
SpeciesList{R <: AbstractRequirement,
  MO <: AbstractMovement, P <: AbstractParams}(numspecies::Int64,
  numtraits::Int64, abun_dist::Distribution, req::R,
  movement::MO, params::P)
```

種の数、彼らが持つ特性の数、彼らの豊富さ、環境からの要求、および彼らの移動カーネルを考慮して、SpeciesListを作成するための関数です。
