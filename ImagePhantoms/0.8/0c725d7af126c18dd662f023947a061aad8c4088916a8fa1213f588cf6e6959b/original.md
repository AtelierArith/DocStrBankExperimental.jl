```
ellipse_parameters(case; fovs::NTuple{2}, u::NTuple{3}, disjoint::Bool)
```

Return vector of Tuples of ellipse parameters. By default the first four elements of each tuple are unitless "fractions of field of view", so elements 1,3 are scaled by `xfov` and elements 2,4 are scaled by `yfov`, where `(xfov, yfov) = fovs`. The optional 3-tuple `u` specifies scaling and/or units:

  * elements 1-4 (center, radii) are scaled by `u[1]` (e.g., mm),
  * elements 5 (angle) is scaled by `u[2]` (e.g., `1` or `°`),
  * elements 6 (value) is scaled by `u[3]` (e.g., `1/cm`) for an attenuation map.

If `disjoint==true` then the middle ellipse positions are adjusted to avoid overlap.
