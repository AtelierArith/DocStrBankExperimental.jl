```
integrate(q0::Quaternion, ω0::Vector, Ib::Matrix, ∆t, torque::Function, N::Integer)
```

Integrate a rotational state ahead by `N` time steps.

Returns `(q1, ω1)`, the orientation and angular velocity after `N` integration steps.
