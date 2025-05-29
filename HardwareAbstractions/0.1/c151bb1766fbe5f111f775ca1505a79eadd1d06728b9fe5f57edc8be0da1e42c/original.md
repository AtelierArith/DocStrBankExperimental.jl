```
y,u,r = run_control_2DOF(process, sysFB[, sysFF]; duration = 10, reference(t) = sign(sin(2π*t)))
```

Perform control experiemnt on process where the feedback and feedforward controllers are given by `sysFB` and `sysFF`, both of type `StateSpace`.

`reference` is a reference generating function that accepts a scalar `t` (time in seconds) and outputs a scalar `r`, default is `reference(t) = sign(sin(2π*t))`.

The outputs `y,u,r` are the beam angle, control signal and reference respectively. ![block diagram](feedback4.png)
