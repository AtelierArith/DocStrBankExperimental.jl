```
mean_ionic_activity_coefficient_sat(model::ESElectrolyteModel,salts,T,m,zsolvent=[1.])
```

Calculate the mean ionic activity coefficient of selection of salts at the saturation point at a certain temperature and molality. These are defined as:

```
γ± = φ±/φ±₀ * ∑zsolv/∑z
```

Example:

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

T = 298.15
m = [1.0]

γ± = mean_ionic_activity_coefficient_sat(model,salts,T,m)
```

If multiple solvents are present, the composition of the solvent can be specified with the `zsolvent` keyword argument.
