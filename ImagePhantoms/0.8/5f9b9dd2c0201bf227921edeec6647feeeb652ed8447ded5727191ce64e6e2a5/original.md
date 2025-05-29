```
ellipsoid_parameters(case; fovs::NTuple{3}, u::NTuple{3})
```

Return vector of Tuples of ellipsoid parameters. By default the parameters are for a 3D Shepp-Logan ellipsoid phantom. By default the first 6 elements of each tuple are unitless "fractions of field of view", so elements 1,4 are scaled by `xfov` and elements 2,5 are scaled by `yfov`, and elements 3,6 are scaled by `zfov`, where `(xfov, yfov, zfov) = fovs`. The optional 3-tuple `u` specifies scaling and/or units:

  * elements 1-6 (center, radii) are scaled by `u[1]` (e.g., mm),
  * elements 7-8 (angles) are scaled by `u[2]` (e.g., `1` or `°`),
  * element 9 (value) is scaled by `u[3]` (e.g., `1/cm`) for an attenuation map.
