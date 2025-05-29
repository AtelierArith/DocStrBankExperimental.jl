```
cposr(str, chars, start)
```

Find the first occurrence in a string of a character belonging to a collection of characters, starting at a specified location, searching in reverse.

### Arguments

  * `str`: Any character string
  * `chars`: A collection of characters
  * `start`: Position to begin looking for one of chars

### Output

Returns the index of the last character of `str` that is one of the characters in string `chars`. Returns -1 if none of the characters was found.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/cposr_c.html)
