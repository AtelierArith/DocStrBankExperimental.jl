```
spk14b(handle, segid, body, center, frame, first, last, chbdeg)
```

Begin a type 14 SPK segment in the SPK file associated with `handle`. See also [`spk14a`](@ref) and [`spk14e`](@ref).

### Arguments

  * `handle`: The handle of an SPK file open for writing
  * `segid`: The string to use for segment identifier
  * `body`: The NAIF ID code for the body of the segment
  * `center`: The center of motion for body
  * `frame`: The reference frame for this segment
  * `first`: The first epoch for which the segment is valid
  * `last`: The last epoch for which the segment is valid
  * `chbdeg`: The degree of the Chebyshev Polynomial used

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/spk14b_c.html)
