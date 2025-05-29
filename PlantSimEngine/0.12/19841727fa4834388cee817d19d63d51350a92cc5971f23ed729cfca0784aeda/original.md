```
variables(pkg::Module)
```

Returns a dataframe of all variables, their description and units in a package that has PlantSimEngine as a dependency (if implemented by the authors).

# Note to developers

Developers of a package that depends on PlantSimEngine should  put a csv file in "data/variables.csv", then this file will be  returned by the function.

# Examples

Here is an example with the PlantBiophysics package:

```julia
#] add PlantBiophysics
using PlantBiophysics
variables(PlantBiophysics)
```
