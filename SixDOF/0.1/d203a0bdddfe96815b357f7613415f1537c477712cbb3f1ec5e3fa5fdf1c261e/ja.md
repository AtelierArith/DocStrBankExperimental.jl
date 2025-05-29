```
sixdof!(ds, s, params, time)
```

動的および運動的ODE。DifferentialEquationsパッケージで使用される形式に従います。

  * s = x, y, z, phi, theta, psi, u, v, w, p, q, r (Stateと同じ順序)
  * params = control, massproperties, reference, aeromodel, propmodel, inertialmodel, atmmodel
