Calculate the specific heat of pure species J/mol-K

# Usage-1:

```
cp(thermo,T)
```

  * thermo::NASAThermo: NASAThermo of the species
  * T::Float64: Temperature in K at which the property is required

# Usage-2:

```
cp(sp,T,thermo,ig)
```

  * sp::String : species name
  * T::Float64 : Temperature K
  * thermoObj::SpeciesThermoObj : Structure of SpeciesThermoObj
  * species_list::Array{String,1}  : List of species
