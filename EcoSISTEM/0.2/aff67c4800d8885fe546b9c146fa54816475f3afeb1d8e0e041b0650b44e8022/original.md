```
SpeciesList{R <: AbstractRequirement, MO <: AbstractMovement,
  T <: AbstractTypes, P <: AbstractParams}(numspecies::Int64,
  numtraits::Int64, abun_dist::Distribution, req::R,
  movement::MO, phy::T, params::P)
```

Function to create a SpeciesList given a number of species, the number of traits they possess, their abundances, requirement from the environment and their movement kernel and any type of AbstractTypes.
