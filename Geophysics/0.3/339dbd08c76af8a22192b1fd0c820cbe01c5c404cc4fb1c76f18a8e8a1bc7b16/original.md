```
freedom(T::Real,G::AbstractMole) = 2heatvolume(T,G)/gasconstant(G)
```

Degrees of freedom `f` with storage energy per mole `gasconstant(G)*T/2` (dimensionless).
