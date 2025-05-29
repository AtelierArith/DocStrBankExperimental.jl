```
dtpool(name)
```

Return the data about a kernel pool variable.

### Arguments

  * `name`: Name of the variable whose value is to be returned

### Output

Returns the tuple `(n ,vartype)`.

  * `n`: Number of values returned for name
  * `vartype`: Type of the variable

      * `:C` if the data is character data
      * `:N` if the data is numeric
      * `:X` if there is no variable name in the pool

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dtpool_c.html)
