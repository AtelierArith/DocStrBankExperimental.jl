```
spk14a(handle, ncsets, coeffs, epochs)
```

Add data to a type 14 SPK segment associated with `handle`. See also [`spk14b`](@ref) and [`spk14e`](@ref).

### Arguments

  * `handle`: The handle of an SPK file open for writing
  * `ncsets`: The number of coefficient sets and epochs
  * `coeffs`: The collection of coefficient sets
  * `epochs`: The epochs associated with the coefficient sets

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spk14a_c.html)
