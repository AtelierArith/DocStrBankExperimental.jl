xy = circlepts(r=1.0; center=(0.0, 0.0), ang1=0.0, ang2=360.0, np=72)

Create an circle in 2D space (see `ellipse3D` if want a circle in the 3D space).

### Args

  * `r`: The circle radius.

### Kwargs

  * `center`: A 2-element array or tuple defining the center of the circle.
  * `ang1`: The starting angle in degrees.
  * `ang2`: The ending angle in degrees.
  * `np`: The number of points to use to define the circle.

### Returns

  * `xy`: A Mx2 matrix of points defining the circle, where M = `np`
