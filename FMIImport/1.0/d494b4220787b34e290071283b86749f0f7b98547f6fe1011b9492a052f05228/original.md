```
unloadFMU(fmu::FMU2, cleanUp::Bool=true; secure_pointers::Bool=true)
```

Unload a FMU. Free the allocated memory, close the binaries and remove temporary zip and unziped FMU model description.

# Arguments

  * `fmu::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `cleanUp::Bool= true`: Defines if the file and directory should be deleted.

# Keywords

  * `secure_pointers=true` whether pointers to C-functions should be overwritten with dummies with Julia assertions, instead of pointing to dead memory (slower, but more user safe)
