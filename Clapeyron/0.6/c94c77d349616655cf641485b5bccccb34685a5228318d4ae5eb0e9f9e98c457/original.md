```
gibbs_solvation(model::EoSModel, T; threaded=true, vol0=(nothing,nothing))
```

Calculates the solvation free energy as:

```julia
g_solv = -R̄*T*log(K)
```

where the first component is the solvent and second is the solute.
