Function to create thermo object. The function reads the therm.dat file and  parses the content based on the ideal gas object to create the thermo data object The function returns SpeciesThermoObj

# Usage:

```
create_thermo(species::Array{T,1}, thermo_file::AbstractString )
```

  * species  : Array of species names
  * thermo_file : name of the thermo file including the path
