This function calculates equilibrium composition based on initial conditions     read from an input filter

# Usage

```
equilibrate(input_file::AbstractString, lib_dir::AbstractString)
```

  * input_file ; input xml file, which specifies T, p, species list, molefracs
  * lib_dir : the folder in which therm.dat file exists

Alternatively the same be calculated based on user input, wherein the species composition is passed as a Dictionary

# Usage

```
equilibrate(T::Float64, p::Float64, species_comp::Dict{String, Float64}, thermo_obj)
```

  * T : Temperature in K
  * p : Pressure in Pa
  * thermo*obj : Thermodynamic object created using IdealGas.create*thermo
  * species_comp : Dictionary of species composition {String, Float64}

Alternatively the same be calculated based on user input where in the species list and molefractions are passed in as separate arrays 

# Usage

```
equilibrate(T, p, thermo_obj, mole_fracs, gasphase)
```

  * T : Temperature in K
  * p : Pressure in Pa
  * thermo*obj : Thermodynamic object created using IdealGas.create*thermo
  * mole_fracs : species mole fractions
  * gasphase : list of gasphase species
