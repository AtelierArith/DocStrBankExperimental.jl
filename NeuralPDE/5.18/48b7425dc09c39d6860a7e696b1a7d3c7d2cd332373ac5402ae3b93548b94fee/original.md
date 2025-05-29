```
build_loss_function(eqs, indvars, depvars, phi, derivative, init_params;
    bc_indvars=nothing)
```

Returns the body of loss function, which is the executable Julia function, for the main equation or boundary condition.
