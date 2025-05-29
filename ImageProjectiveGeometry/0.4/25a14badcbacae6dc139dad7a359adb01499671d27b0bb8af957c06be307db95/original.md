inveuler - Inverse of Euler transform

```
Usage:  (euler1, euler2) = inveuler(T)

Argument:  T - 4x4 Homogeneous transformation matrix or 3x3 rotation matrix

Returns: euler1 = [phi1, theta1, psi1] - the 1st solution and,
         euler2 = [phi2, theta2, psi2] - the 2nd solution

     rotz(phi1)   * roty(theta1)    * rotz(psi1)      = T
  rotz(euler1[1]) * roty(euler1[2]) * rotz(euler1[3]) = T
```

See also: invrpy(), invht(), rotx(), roty(), rotz()
