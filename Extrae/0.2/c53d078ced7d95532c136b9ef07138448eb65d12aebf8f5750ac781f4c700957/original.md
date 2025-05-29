```
setoption(options)
```

Configure tracing options at runtime. The options parameter has to be a bitwise or combination of the following options, depending on the user's needs:

  * EXTRAE*CALLER*OPTION Dumps caller information at each entry or exit point of the MPI routines. Caller levels need to be configured at XML.
  * `EXTRAE_HWC_OPTION` Activates hardware counter gathering.
  * `EXTRAE_MPI_OPTION` Activates tracing of MPI calls.
  * `EXTRAE_MPI_HWC_OPTION` Activates hardware counter gathering in MPI routines.
  * `EXTRAE_OMP_OPTION` Activates tracing of OpenMP runtime or outlined routines.
  * `EXTRAE_OMP_HWC_OPTION` Activates hardware counter gathering in OpenMP runtime or outlined routines.
  * `EXTRAE_UF_HWC_OPTION` Activates hardware counter gathering in the user functions.
