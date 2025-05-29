```
setForce!(mechanism, eqconstraint, Fτ)
```

Sets the minimal coordinate forces (vector) of joint `eqconstraint`.

Prismatic joint example:     setVelocity!(mechanism, geteqconstraint(mechanism, jointid), [-1.0])
