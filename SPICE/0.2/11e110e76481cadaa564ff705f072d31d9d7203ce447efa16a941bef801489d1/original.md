```
ncposr(str, chars, start)
```

Find the first occurrence in a string of a character NOT belonging to a collection of characters, starting at a specified location, searching in reverse.

### Arguments

  * `str`: A string
  * `chars`: A collection of characters
  * `start`: Position to begin looking for a character not in `chars`

### Output

Returns the index of the last character of `str` at or before index `start` that is not in the collection `chars`.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/ncposr_c.html)
