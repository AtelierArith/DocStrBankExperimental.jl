```
ngrid(Nx,Ny,use_cude=false)
```

Computes the orders n of the plane wave expansion

# Arguments

  * `Nx` : Maximum order in x
  * `Ny` : Maximum order in y
  * `use_cuda` : optional, switch to CUDA GPU solver

# Outputs

  * `nx` : Order in x
  * `ny` : Order in y
  * `dnx` : Differential order in x
  * `dny` : Differential order in y
