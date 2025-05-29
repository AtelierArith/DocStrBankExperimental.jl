```
variable_gamma(de, Pt, group)
```

Generate proposal according to θ' = θt + γ(θm − θn) + b where γ = 2.38/√(2d) where d is the number of parameters

# Arguments

  * `de`: differential evolution object
  * `Pt`: current particle
  * `group`: a group of particles
