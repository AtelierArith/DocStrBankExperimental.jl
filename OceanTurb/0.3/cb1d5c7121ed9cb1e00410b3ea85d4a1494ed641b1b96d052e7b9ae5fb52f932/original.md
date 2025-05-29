```
Equation(R, K)
```

Construct an Equation that represents a PDE of the form

```
∂ϕ/∂t = ∂/∂z (K ∂ϕ/∂z) + R ,
```

so that K is a diffusivity and R captures 'remaining' terms.

In OceanTurb, K and R are tuples of functions. The functions K[j](m, i) and R[j](m, i) calculate the diffusivity K and remaining terms R for the model `m` at grid point `i`.
