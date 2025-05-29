```
fmi2GetTypesPlatform(fmu::FMU2)
```

Returns the string to uniquely identify the “fmi2TypesPlatform.h” header file used for compilation of the functions of the FMU. The standard header file, as documented in this specification, has fmi2TypesPlatform set to “default” (so this function usually returns “default”).

# Arguments

  * `fmu::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.

# Returns

  * Returns the string to uniquely identify the “fmi2TypesPlatform.h” header file used for compilation of the functions of the FMU.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.4 Inquire Platform and Version Number of Header Files
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
