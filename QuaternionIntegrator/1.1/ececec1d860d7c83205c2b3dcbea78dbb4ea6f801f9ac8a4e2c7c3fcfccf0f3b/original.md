```
integrate(q0::Quaternion, ω0::Vector, Ib::Matrix, ∆t, torque::Function ; IbInv::Union{Nothing,AbstractArray} = nothing)
```

Integrate a rotational state ahead by one time step.

  * `q0`, current orientation quaternion.
  * `ω0`, current angular velocity (length-3 vector).
  * `Ib`, inertial tensor of the object in body coordinates (3×3 matrix).
  * `∆t`, length of time step.
  * `torque`, a function that returns a (length-3) torque vector given an orientation.
  * `IbInv` is an optional parameter giving the inverse matrix of `Ib`. Providing it will speed up the computation slightly.

Returns `(q1, ω1)`, the orientation and angular velocity at the end of the time step.

Using the Unitful package, all inputs can have units, all the mathematics are done with units and the return values will have correct units.

  * `q0` is dimensionless.
  * `ω0` has dimension of 1/time (SI: 1/second)
  * `Ib` has dimension mass * length^2 (SI: kilogram * meter^2)
  * `∆t` has dimension of time (SI: second)
  * `torque` returns a value with dimension of torque (SI: Newton * meter)
