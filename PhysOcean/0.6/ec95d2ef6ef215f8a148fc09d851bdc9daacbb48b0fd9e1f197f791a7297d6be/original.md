```
rhoi = integraterhoprime(rhop,z,dim=ndims(rhop))
```

Integrates density anomalies over depth. When used with gravity, assuming gravity is independant on z, it can be used to calculate dynamic pressure up to a constant. Function can be used with 1D, 2D, ...

# Input:

  * `rhop`: density anomaly array
  * `z`: vertical position array. Zero at surface and positive downward, same dimensions as rhop
  * `dim`: along which dimension depth is found and integral is performed. If not provided, last dimension is taken

# Output:

  * `rhoi` : Integrated value to the same levels as on which rhop where given. So basically total density anomaly ABOVE the current depth

# Note:

Compute vertical integral of density anomalies
