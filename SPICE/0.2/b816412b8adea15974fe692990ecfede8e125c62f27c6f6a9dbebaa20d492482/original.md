```
badkpv(caller, name, comp, size, divby, typ)
```

Determine if a kernel pool variable is present and if so that it has the correct size and type.

### Arguments

  * `caller`: Name of the routine calling this routine
  * `name`: Name of a kernel pool variable
  * `comp`: Comparison operator
  * `size`: Expected size of the kernel pool variable
  * `divby`: A divisor of the size of the kernel pool variable
  * `type`: Expected type of the kernel pool variable

### Output

The function returns `false` if the kernel pool variable is OK otherwise an exception is thrown.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/badkpv_c.html)
