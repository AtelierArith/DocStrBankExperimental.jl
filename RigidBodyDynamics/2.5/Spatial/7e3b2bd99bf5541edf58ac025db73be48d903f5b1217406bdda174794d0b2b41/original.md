```julia
struct GeometricJacobian{A<:(AbstractMatrix)}
```

A geometric Jacobian (also known as basic, or spatial Jacobian) maps a vector of joint velocities to a twist.
