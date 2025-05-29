```julia
rebaseFactorVariable!(
    dfg,
    fctsym,
    newvars;
    rmDisconnected,
    autoinit
)

```

Helper function to modify factor connectivity to variables.

Notes

  * Developed for updating a dead reckoning odometry factor.
  * Arguments are order sensitive.
