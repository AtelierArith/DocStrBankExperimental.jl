```
valid!(set::SpiceCell{T}) where T
```

Create a valid SPICE set from a SPICE Cell of any data type.

### Arguments

  * `set`: Set to be validated

### Output

Returns the validated set with ordered elements and duplicates removed.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/valid_c.html)
