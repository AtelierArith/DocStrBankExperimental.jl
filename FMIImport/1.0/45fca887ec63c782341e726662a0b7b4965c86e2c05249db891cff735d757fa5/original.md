```
fmi2GetVersion(fmu::FMU2)
```

Returns the version of the “fmi2Functions.h” header file which was used to compile the functions of the FMU.

# Arguments

  * `fmu::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.

# Returns

  * Returns a string from the address of a C-style (NUL-terminated) string. The string represents the version of the “fmi2Functions.h” header file which was used to compile the functions of the FMU. The function returns “fmiVersion” which is defined in this header file. The standard header file as documented in this specification has version “2.0”

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.4 Inquire Platform and Version Number of Header Files
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
