Determine time intervals when the angular separation between the position vectors of two target bodies relative to an observer satisfies a numerical relationship.

### Arguments

  * `targ1`: Name of first body
  * `shape1`: Name of shape model describing the first body
  * `frame1`: The body-fixed reference frame of the first body
  * `targ2`: Name of second body
  * `shape2`: Name of the shape model describing the second body
  * `frame2`: The body-fixed reference frame of the second body
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of the observing body
  * `relate`: Operator that either looks for an extreme value (max, min, local, absolute) or compares   the angular separation value and refval
  * `refval`: Reference value
  * `adjust`: Absolute extremum adjustment value
  * `step`: Step size in seconds for finding angular separation events
  * `nintvls`: Workspace window interval count
  * `cnfine`: Window to which the search is restricted

### Output

Returns a window containing the results.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfsep_c.html)
