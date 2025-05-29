```
mean_ionic_activity_coefficient(model::ESElectrolyteModel,salts,p,T,m,zsolvent=[1.])
```

Calculate the mean ionic activity coefficient of selection of salts at a given pressure, temperature and molality. These are defined as:

```
γ± = φ±/φ±₀ * ∑zsolv/∑z
```

Example:

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

p = 1e5
T = 298.15
m = [1.0]

γ± = mean_ionic_activity_coefficient(model,salts,p,T,m)
```

If multiple solvents are present, the composition of the solvent can be specified with the `zsolvent` keyword argument.
