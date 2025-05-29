```
gfevnt(udstep, udrefn, gquant, qnpars, lenvals, qpnams, qcpars, qdpars, qipars, qlpars,
       op, refval, tol, adjust, rpt, udrepi, udrepu, udrepf, nintvls, bail, udbail, cnfine)
```

Determine time intervals when a specified geometric quantity satisfies a specified mathematical condition.

### Arguments

  * `udstep`: Name of the routine that computes and returns a time step
  * `udrefn`: Name of the routine that computes a refined time
  * `gquant`: Type of geometric quantity
  * `qpnams`: Names of quantity definition parameters
  * `qcpars`: Array of character quantity definition parameters
  * `qdpars`: Array of double precision quantity definition parameters
  * `qipars`: Array of integer quantity definition parameters
  * `qlpars`: Array of logical quantity definition parameters
  * `op`: Operator that either looks for an extreme value (max, min, local, absolute) or compares the   geometric quantity value and a number
  * `refval`: Reference value
  * `tol`: Convergence tolerance in second
  * `adjust`: Absolute extremum adjustment value
  * `rpt`: Progress reporter on (`true`) or off (`false`)
  * `udrepi`: Function that initializes progress reporting
  * `udrepu`: Function that updates the progress report
  * `udrepf`: Function that finalizes progress reporting
  * `nintvls`: Workspace window interval coun
  * `cnfine`: SPICE window to which the search is restricted

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfevnt_c.html)
