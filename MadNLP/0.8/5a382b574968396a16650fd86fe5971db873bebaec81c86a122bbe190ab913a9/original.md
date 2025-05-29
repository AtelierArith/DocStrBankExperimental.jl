```
solve!(kkt::AbstractKKTSystem, w::AbstractKKTVector)
```

Solve the KKT system $K x = w$ with the linear solver stored inside `kkt` and stores the result inplace inside the `AbstractKKTVector` `w`.
