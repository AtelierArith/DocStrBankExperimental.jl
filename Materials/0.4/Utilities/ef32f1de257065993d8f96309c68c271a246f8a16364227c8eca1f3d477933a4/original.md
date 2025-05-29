```
isotropic_compliance_tensor(lambda::T, mu::T) where T <: Real
```

Compute the compliance tensor S(i,j,k,l) (rank 4, symmetric) for an isotropic material having the Lamé parameters `lambda` and `mu`.

If you have (E, nu) instead, use `lame` to get (lambda, mu).
