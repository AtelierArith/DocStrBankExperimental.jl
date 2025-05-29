Evaluates the spline at a point. The point can be specified as a Real number (Int, Float, etc) or a Date. Derivatives can also be taken.

### Inputs

  * `spline` - A `Schumaker` type spline
  * `PointToExamine` - The point at which to evaluate the integral
  * `derivative` - The derivative being sought. This should be 0 to just evaluate the spline, 1 for the first derivative or 2 for a second derivative.

Higher derivatives are all zero (because it is a quadratic spline). Negative values do not give integrals. Use evaluate_integral instead.

### Returns

  * A value of the spline or appropriate derivative in the same format as specified in the spline.
