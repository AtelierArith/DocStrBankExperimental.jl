```
multiphase_projection!(solver::MultiphaseSolver)
```

Solve the linear system to find an orthogonal projection of `dv` to a constraint space which gurantees conservation of area for every fluid phase. You only need this for multiphase flows. You can also run multiphase problems without it but expect some artificial density ridges between phases of different densities.
