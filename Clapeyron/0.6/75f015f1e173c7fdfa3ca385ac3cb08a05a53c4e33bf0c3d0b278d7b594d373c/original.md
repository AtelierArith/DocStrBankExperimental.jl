```
acentric_factor(model::EoSModel;crit = crit_pure(model), satmethod = ChemPotVSaturation())
```

calculates the acentric factor using its definition:

```
ω = -log10(psatᵣ) -1, at Tᵣ = 0.7
```

To do so, it calculates the critical temperature (using `crit_pure`) and performs a saturation calculation (with `saturation_pressure(model,0.7Tc,satmethod)`)
