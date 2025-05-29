```
online(apt::Adapt_MZI; target::Symbol=:sharpness, output::String="phi")
```

Online adaptive phase estimation in the MZI.

  * `apt`: Adaptive MZI struct which contains x, p, and rho0.
  * `target`: Setting the target function for calculating the tunable phase. Options are: "sharpness" and "MI".
  * `output`: Choose the output variables. Options are: "phi" and "dphi".
