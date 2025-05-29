```
srcwa_flows(a,b,em,kz0)
```

Computes the powers flow in z direction at multiple interfaces

# Arguments

  * `a` :  array of forward wave amplitude vectors at all interfaces
  * `b` :  array of backward wave amplitude vectors at all interfaces
  * `V0` :  magnetic field eigenmodes of free space
  * `kz0` :  z-component of the impinging wave vector (for normalization)

# Outputs

  * `flow` : array of power flows in the z direction at all interfaces
