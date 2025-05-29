```
SolitarySGN(param; x₀=0)
```

Build the initial data associated with `SolitaryWaveSerreGreenNaghdi(param; x₀=0)`, of type `InitialData`, to be used in initial-value problems `Problem(model, initial::InitialData, param)`.

---

```
SolitarySGN(c; ϵ=1,μ=1,x₀=0,N=2^12)
```

Build the initial data with velocity `c`, center `x₀`, dimensionless parameters `ϵ` and `μ`, and number of collocation points `N`.
