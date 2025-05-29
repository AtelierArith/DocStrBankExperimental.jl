```
kxtrct(keywd, terms, string)
```

Locate a keyword in a string and extract the substring from the beginning of the first word following the keyword to the beginning of the first subsequent recognized terminator of a list.

### Arguments

  * `keywd`: Word that marks the beginning of text of interest
  * `terms`: Set of words, any of which marks the end of text
  * `string`: String containing a sequence of words

### Output

Returns `nothing` if `keywd` was found or a tuple consisting of

  * `string`: The input `string` with the text of interest removed
  * `substr`: String from end of `keywd` to beginning of first `terms` item found

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/kxtrct_c.html)
