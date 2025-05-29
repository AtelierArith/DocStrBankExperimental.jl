```
lx4sgn(string, first)
```

Scan a string from a specified starting position for the end of a signed integer.

### Arguments

  * `string`: Any character string
  * `first`: First character to scan from in string

### Output

  * `last`: Last character that is part of a signed integer. If there is no such         character, `last` will be returned with the value `first-1`.
  * `nchar`: Number of characters in the signed integer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lx4sgn_c.html)
