```
body_accelerations(system, x=system.x; linear_acceleration=zeros(3), angular_acceleration=zeros(3))
```

Extract the linear and angular acceleration of the body frame from the state vector, if applicable.  Otherwise return the provided linear and angular acceleration.  This function is applicable only for steady state and initial condition analyses.
