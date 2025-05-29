```
xfmsta(input_state, input_coord_sys, output_coord_sys, body)
```

Transform a state between coordinate systems.

### Arguments

  * `input_state`: Input state
  * `input_coord_sys`: Current (input) coordinate system
  * `output_coord_sys`: Desired (output) coordinate system
  * `body`: Name or NAIF ID of body with which coordinates are associated (if applicable)

### Output

Returns the converted output state.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/xfmsta_c.html)
