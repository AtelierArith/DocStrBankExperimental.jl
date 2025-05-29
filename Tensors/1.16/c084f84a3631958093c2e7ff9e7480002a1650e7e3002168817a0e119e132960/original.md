```
rotation_tensor(ψ::Number, θ::Number, ϕ::Number)
```

Return the three-dimensional rotation matrix corresponding to the rotation described by the three Euler angles $ψ$, $θ$, $ϕ$.

$$
R(ψ,θ,ϕ) = R_x(ψ)R_y(θ)R_z(ϕ)
$$

see e.g. [http://eecs.qmul.ac.uk/~gslabaugh/publications/euler.pdf](http://eecs.qmul.ac.uk/~gslabaugh/publications/euler.pdf) for a complete description.

Note that the [gimbal lock phenomena](https://en.wikipedia.org/wiki/Gimbal_lock) can occur when using this rotation tensor parametrization.
