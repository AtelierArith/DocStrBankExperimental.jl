S(thermo::NASAThermo, T::Float64) Calculates the entropy of pure species J/mol-K

# Usage-1:

```
S(thermo,T)
```

  * thermo::NASAThermo: NASAThermo of the species
  * T::Float64: Temperature in K at which the property is required

# Usage-2:

```
S(sp,T,thermo,ig)
```

  * sp::String : species name
  * T::Float64 : Temperature K
  * thermo::SpeciesThermoObj : Structure of SpeciesThermoObj
  * species_list::Array{String,1}  : List of species
