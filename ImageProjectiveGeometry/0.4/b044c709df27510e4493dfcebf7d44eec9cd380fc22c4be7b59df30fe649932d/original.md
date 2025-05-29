invrpy - Inverse of Roll Pitch Yaw transform

```
Usage:  (rpy1, rpy2) = invrpy(RPY)
 
Argument:  RPY - 4x4 Homogeneous transformation matrix or 3x3 rotation matrix

Returns:  rpy1 = [phi1, theta1, psi1] - the 1st solution and
          rpy2 = [phi2, theta2, psi2] - the 2nd solution

   rotz(phi1)  * roty(theta1)  * rotx(psi1)    = RPY
 rotz(rpy1[1]) * roty(rpy1[2]) * rotx(rpy1[3]) = RPY
```

See also: inveuler(), invht(), rotx(), roty(), rotz()
