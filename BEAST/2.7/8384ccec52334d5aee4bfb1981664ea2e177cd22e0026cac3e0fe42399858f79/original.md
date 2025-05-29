```
laplace_to_z(rho, n, N, dt, A, b)
```

Returns the complex matrix valued Laplace variable s that correspond to the variable z = rho*exp(2*im*pi*n/N) for a given Butcher tableau (A,b,c) and a time step dt.
