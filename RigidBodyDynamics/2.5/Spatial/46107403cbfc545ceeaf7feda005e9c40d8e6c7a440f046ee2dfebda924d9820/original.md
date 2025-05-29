```julia
newton_euler(inertia, spatial_accel, twist)

```

Apply the Newton-Euler equations to find the external wrench required to make a body with spatial inertia $I$, which has twist $T$ with respect to an inertial frame, achieve spatial acceleration $\dot{T}$.

This wrench is also equal to the rate of change of momentum of the body.
