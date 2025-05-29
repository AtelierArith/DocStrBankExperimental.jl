newprojection(ipos::Point3D, center::Point3D, up::Point3D, perspective=0.0)

Define a new Projection:

  * ipos is the eye position
  * center is the 3D point to appear in the center of the 2D image
  * up is a point that is to appear vertically above the center

If `perspective` is 0.0 (the default) the projection is parallel. Otherwise it's a vague magnification factor for perspective projections.

The three vectors U, V, W, and the three scalar products, ue, ve, and we:

  * U is at right angles to line of sight w, and to t-e, so it corresponds to

the x axis of the 2D image

  * V is at right angles to u and to the line of sight, so it's the y axis of the

2D image

  * W is the line of sight
  * we is the projection of the eye position onto w
  * ue is the projection of the eye position onto that x-axis
  * ve is the projection of the eye position onto that y axis
