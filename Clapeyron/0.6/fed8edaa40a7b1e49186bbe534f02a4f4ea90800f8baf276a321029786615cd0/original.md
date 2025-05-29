```
osmotic_coefficient_sat(model::ESElectrolyteModel,salts,T,m,zsolvent=[1.])
```

Calculate the osmotic coefficient of selection of solvents at the saturation point at a certain temperature and molality. These are defined as:

```
ϕ = -1/(∑νi*mi*Mw)*log(asolv)
```

Example:

```julia
model = ePCSAFT(["water"],["sodium","chloride"])

salts = [("sodium chloride",("sodium"=>1,"chloride"=>1))]

T = 298.15
m = [1.0]

ϕ = osmotic_coefficient(model,salts,T,m)
```

If multiple solvents are present, the composition of the solvent can be specified with the `zsolvent` keyword argument.
