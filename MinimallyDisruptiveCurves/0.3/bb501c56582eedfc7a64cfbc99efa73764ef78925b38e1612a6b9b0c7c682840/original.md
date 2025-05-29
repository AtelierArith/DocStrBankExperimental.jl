```
MomentumReadjustment(tol::AbstractFloat, verbose::Bool)
```

Ideally, dHdu = 0 throughout curve evolution, where H is the Hamiltonian/momentum, and u is the curve velocity in parameter space. Numerical error integrates and prevents this. This struct readjusts momentum when `abs(dHdu) > tol`, so that `dHdu = 0` is recovered. 
