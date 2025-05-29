```
add_measurement_disturbance(sys::StateSpace{Continuous}, Ad::Matrix, Cd::Matrix)
```

システムを作成する

```
Ae = [A 0; 0 Ad]
Be = [B; 0]
Ce = [C Cd]
```
