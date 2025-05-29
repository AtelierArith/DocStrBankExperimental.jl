```
setVelocity!(mechanism, eqconstraint, vω)
```

Sets the minimal coordinate velocities (vector) of joint `eqconstraint`.

Planar joint example:     setVelocity!(mechanism, geteqconstraint(mechanism, jointid), [0.5;2.0])
