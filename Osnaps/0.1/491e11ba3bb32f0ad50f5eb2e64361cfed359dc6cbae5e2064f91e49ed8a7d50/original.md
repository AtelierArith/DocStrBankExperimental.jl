```
minimizer(nd::Int; np::Int=35*ND, ne::Int=ND+1, ny::Int=0, method::String="global")
```

An interface function to create/initialize an object for the minimization.

## Arguments:

  * `nd`:     Dimension of parameters to be minimized.
  * `np`:     Desired population size (*optional*).
  * `ne`:     Desired size of elites (*optional*).
  * `ny`:     Size of data space (required for *variational-inference*).
  * `method`: Desired algorithm ("global", "variational-inference").
