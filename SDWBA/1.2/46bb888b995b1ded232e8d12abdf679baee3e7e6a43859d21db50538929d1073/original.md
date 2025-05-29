Construct a data structure describing a fluid-like weak scatterer with a deformed cylindrical shape.  This shape is approximated by a series of `N` discrete segments, described by the [x, y, z] coordinates, radii, and material properties at their endpoints.

#### Parameters

  * `r` : 3x`N` matrix describing the scatterer's centerline.  Each column is the

location in 3-D space of one of the centerline points (these should be arranged in the proper order).

  * `a` : Vector of radii, length `N`.
  * `h`, `g` : Vectors of sound speed and density contrasts (i.e., the ratio

of sound speed or density inside the scatter to the same quantity in the surrounding medium).
