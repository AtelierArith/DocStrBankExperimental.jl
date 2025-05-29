```
EmbeddedODESolution(sol::AbstractODESolution, Embedding::Function) -> AbstractODESolution
EmbeddedODESolution(sol::AbstractODESolution, PL::Plane) -> AbstractODESolution
```

Maps the solution `sol(t)` to some ODE into a larger space via `Embedding∘sol`.
