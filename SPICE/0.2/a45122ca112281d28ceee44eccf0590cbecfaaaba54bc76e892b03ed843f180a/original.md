```
scard!(cell::SpiceCell{T}, card) where T
```

Set the cardinality of a cell.

### Arguments

  * `cell`: The cell
  * `card`: Cardinality of (number of elements in) the cell

### Output

Returns `cell` with its cardinality set to `card`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/scard_c.html)
