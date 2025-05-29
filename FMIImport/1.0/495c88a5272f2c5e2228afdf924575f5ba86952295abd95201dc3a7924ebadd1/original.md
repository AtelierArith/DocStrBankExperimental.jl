```
fmi3GetVersion(fmu::FMU3)
```

# Arguments

  * `fmu::FMU3`: Mutable struct representing a FMU and all it instantiated instances in the FMI 3.0 Standard.

# Returns

  * Returns a string from the address of a C-style (NUL-terminated) string. The string represents the version of the “fmi3Functions.h” header file which was used to compile the functions of the FMU. The function returns “fmiVersion” which is defined in this header file. The standard header file as documented in this specification has version “3.0”

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4. Inquire Version Number of Header Files
