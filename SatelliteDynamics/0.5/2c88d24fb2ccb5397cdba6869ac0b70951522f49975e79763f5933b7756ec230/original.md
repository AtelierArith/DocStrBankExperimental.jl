The `EulerAngle` type provides a represenation of EulerAngles for storing attitude information.

Valid sequences are: `121, 123, 131, 132, 212, 213, 231, 232, 312, 313, 321, 323`.

Data members:

  * `seq::Integer`: Order of application of angles with respect to body axis.
  * `phi::Float64`: First Euler angle
  * `theta::Float64`: Second Euler angle
  * `psi::Float64`: Third Euler angle

References:

1. J. Diebel, *Representing attitude: Euler angles, unit quaternions, and rotation vectors.* Matrix 58(15-16) (2006).
