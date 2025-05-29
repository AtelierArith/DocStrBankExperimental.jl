```
struct LagrangianAlgorithm <: CombinatorialAlgorithm
```

Use Lagrangian relaxation to solve the instance, followed by a refinement step  and more iterations as required. This is especially useful to build an algorithm  for a problem with a new constraint based on other algorithms. These techniques  often yield an constant multiplicative approximation, based on Lagrangian  relaxation and refinement.
