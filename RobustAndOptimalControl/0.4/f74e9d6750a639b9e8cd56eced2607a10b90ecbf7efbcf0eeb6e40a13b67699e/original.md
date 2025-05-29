```
add_measurement_disturbance(sys::StateSpace{Continuous}, Ad::Matrix, Cd::Matrix)
```

Create the system

```
Ae = [A 0; 0 Ad]
Be = [B; 0]
Ce = [C Cd]
```
