```
SolitaryWhitham(param; kwargs)
```

Build the initial data associated with `SolitaryWaveWhitham(param; kwargs)`, of type `InitialData`, to be used in initial-value problems `Problem(model, initial::InitialData, param)`.

---

```
SolitaryWhitham(c; ϵ=1,μ=1,N=2^12,kwargs)
```

Build the initial data with velocity `c`, dimensionless parameters `ϵ` and `μ`, and number of collocation points `N`, and `kwargs` the other (optional) keyword arguments as above.
