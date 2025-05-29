```
utility_matrices(basis::NodalBasis{Line})
```

Return the matrices

  * `D`, derivative matrix
  * `M`, mass matrix
  * `R`, restriction matrix (interpolation to the boundaries)
  * `B`, boundary normal matrix
  * `MinvRtB = M \ R' * B`

used in the formulation of flux reconstruction / correction procedure via reconstruction using summation-by-parts operators, cf. Ranocha, Öffner, Sonar (2016) Summation-by-parts operators for correction procedure via reconstruction, Journal of Computational Physics 311, 299-328.
