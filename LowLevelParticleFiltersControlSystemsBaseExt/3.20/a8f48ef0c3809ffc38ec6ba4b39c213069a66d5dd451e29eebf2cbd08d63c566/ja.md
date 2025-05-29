```
KalmanFilter(sys::StateSpace{Discrete}, R1, R2, d0 = MvNormal(Matrix(R1)); kwargs...)
```

ControlSystems.jlからの事前定義された`StateSpace`システムから`KalmanFilter`を構築します。
