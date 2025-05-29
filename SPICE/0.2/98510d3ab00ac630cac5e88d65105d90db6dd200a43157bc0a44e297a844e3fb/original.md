```
gfrefn(t1, t2, s1, s2)
```

For those times when we can't do better, we use a bisection method to find the next time at which to test for state change.

### Arguments

  * `t1`: One of two values bracketing a state change
  * `t2`: The other value that brackets a state change
  * `s1`: State at `t1`
  * `s2`: State at `t2`

### Output

Returns the new value at which to check for transition.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfrefn_c.html)
