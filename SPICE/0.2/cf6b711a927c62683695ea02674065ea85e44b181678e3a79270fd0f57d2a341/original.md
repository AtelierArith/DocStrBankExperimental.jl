```
dasec(handle; bufsiz=256, lenout=1024)
```

Extract comments from the comment area of a binary DAS.

### Arguments

  * `handle`: Handle of binary DAS opened with read access
  * `bufsiz`: Maximum size, in lines, of buffer (default: 256)
  * `lenout`: Length of strings in output buffer (default: 1024)

### Output

Returns a buffer where extracted comment lines are placed.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/dasec_c.html)
