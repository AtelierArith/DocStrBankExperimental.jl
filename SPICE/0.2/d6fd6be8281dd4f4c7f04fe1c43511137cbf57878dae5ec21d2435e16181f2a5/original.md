```
lx4dec(string, first)
```

Scan a string from a specified starting position for the end of a decimal number.

### Arguments

  * `string`: Any character string
  * `first`: First character to scan from in string

### Output

  * `last`: Last character that is part of a decimal number. If there is no such         character, `last` will be returned with the value `first-1`.
  * `nchar`: Number of characters in the decimal number

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/lx4dec_c.html)
