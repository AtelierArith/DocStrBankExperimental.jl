```
ExogenousDOF() <: AbstractDOFKinematics
```

Sets a DOF as constrained, but with its behavior set by an exogenous process at every instant. For such a DOF, one must provide a vector  `[x,ẋ,ẍ]`.
