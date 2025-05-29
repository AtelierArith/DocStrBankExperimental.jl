Cumulative density function of the Tracy-Widom distribution.

Computes the Tracy-Widom distribution by Bornemann's method of evaluating a finite dimensional approximation to the Fredholm determinant using quadrature.

doi.org/10.1090/S0025-5718-09-02280-7

# Arguments

  * `d::TracyWidom` or `Type{TracyWidom}`: an instance of `TracyWidom` or the type itself
  * `s::Real`: The point at which to evaluate the cdf
  * `num_points::Integer = 25`: The number of points in the quadrature
