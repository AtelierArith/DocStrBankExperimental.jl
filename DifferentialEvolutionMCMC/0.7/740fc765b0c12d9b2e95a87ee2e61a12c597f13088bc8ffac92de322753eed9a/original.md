```
random_gamma(de, Pt, group)
```

Generate proposal according to θ' = θt + γ1(θm − θn) + γ2(θb − θt) + b. γ2=0 after burnin

# Arguments

  * `de`: differential evolution object
  * `Pt`: current particle
  * `group`: a group of particles
