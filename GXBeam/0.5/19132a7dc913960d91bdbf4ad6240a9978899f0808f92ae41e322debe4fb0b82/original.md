```
PrescribedConditions{T}
```

Type which defines the prescribed displacements and loads at a point.

# Fields:

  * `pd`: Flag for each degree of freedom indicating whether displacements are prescribed
  * `pl`: Flag for each degree of freedom indicating whether loads are prescribed
  * `u`: Linear displacement
  * `theta`: Angular displacement
  * `F`: External forces
  * `M`: External moments
  * `Ff`: Follower forces
  * `Mf`: Follower moments
