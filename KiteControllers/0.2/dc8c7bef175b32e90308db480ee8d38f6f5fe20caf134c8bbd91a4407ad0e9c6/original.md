```
function calc_steering(fpc, parking)
```

Calculate the steering output u*s and the turn rate error err, but also the signals Kpsi*out, Ku*out and int*in.

Implements the simulink block diagram, shown in: 01*doc/flight*path*controller*I.png

If the parameter parking is true, only the heading is controlled, not the course.
