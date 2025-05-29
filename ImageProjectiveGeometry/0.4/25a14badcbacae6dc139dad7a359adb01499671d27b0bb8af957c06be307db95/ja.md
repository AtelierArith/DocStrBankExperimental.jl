inveuler - オイラー変換の逆

```
Usage:  (euler1, euler2) = inveuler(T)

Argument:  T - 4x4 同次変換行列または 3x3 回転行列

Returns: euler1 = [phi1, theta1, psi1] - 1つ目の解と、
         euler2 = [phi2, theta2, psi2] - 2つ目の解

     rotz(phi1)   * roty(theta1)    * rotz(psi1)      = T
  rotz(euler1[1]) * roty(euler1[2]) * rotz(euler1[3]) = T
```

See also: invrpy(), invht(), rotx(), roty(), rotz()
