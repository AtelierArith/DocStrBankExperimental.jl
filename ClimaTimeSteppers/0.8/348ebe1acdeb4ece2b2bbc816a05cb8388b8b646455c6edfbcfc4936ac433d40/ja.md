```
ForwardEulerODEFunction(f; jac_prototype, Wfact, tgrad)
```

`f(un, u, p, t, dt)` が前進オイラー更新を提供するODE関数ラッパー

```
un .= u .+ dt * f(u, p, t)
```
