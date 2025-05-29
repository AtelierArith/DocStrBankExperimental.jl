```
UnconstrainedDOF([f::Function]) <: AbstractDOFKinematics
```

Sets a DOF as unconstrained, so that its behavior is either completely free or determined by a given force response (e.g., spring and/or damper). This force response is set by the optional input function `f`. The signature of `f` must be `f(x,xdot,t)`, where `x` and `xdot` are the position of the dof and its derivative, respectively, and `t` is the current time. It must return a single scalar, serving as a force or torque for that DOF.
