```
setPosition!(mechanism, eqconstraint, xθ)
```

Sets the minimal coordinates (vector) of joint `eqconstraint`. 

Revolute joint example:     setPosition!(mechanism, geteqconstraint(mechanism, "joint_name"), [pi/2])
