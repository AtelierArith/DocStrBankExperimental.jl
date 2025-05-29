```
SpeciesList{R <: AbstractRequirement, MO <: AbstractMovement,
  T <: AbstractTypes, P <: AbstractParams}(numspecies::Int64,
  numtraits::Int64, abun_dist::Distribution, req::R,
  movement::MO, phy::T, params::P)
```

種の数、持っている特性の数、豊富さ、環境からの要求、移動カーネル、および任意のタイプのAbstractTypesを考慮してSpeciesListを作成する関数です。
