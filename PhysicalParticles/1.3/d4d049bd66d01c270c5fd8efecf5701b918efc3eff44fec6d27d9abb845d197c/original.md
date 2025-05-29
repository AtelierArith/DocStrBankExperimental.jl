rotate(p::PVector, vec::PVector, θ::Number)

Rotate `p` around direction vector `vec` by angle `θ`.

For normalized `vec = (x, y, z)`, the rotation matrix:

```
            |  cos(θ) + (1-cos(θ))*x^2   (1-cos(θ))*x*y - sin(θ)*z  (1-cos(θ))*x*z + sin(θ)*y |
M(vec, θ) = | (1-cos(θ))*y*x + sin(θ)*z   cos(θ) + (1-cos(θ))*y^2   (1-cos(θ))*y*z - sin(θ)*x |
            | (1-cos(θ))*z*x - sin(θ)*y  (1-cos(θ))*z*y + sin(θ)*x   cos(θ) + (1-cos(θ))*z^2  |
```
