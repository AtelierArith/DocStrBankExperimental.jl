```
LotkaVolterra(;kwargs)
```

Create a sample dataset using the Lotka-Volterra predator-prey model as its process model:

````
```math
rac{dN}{dt} = rN - lpha NP \
rac{dP}{dt} = 	hetalpha NP - mP
```
````

and an observation error following a normal distribution with mean 0 and standard deviation σ.

```
# kwargs
- `plot`: Does the function return a plot? Default is `true`.
- `seed`: Seed for observation error to create repeatable examples. Default is `123`.
- `datasize`: Number of time steps generated. Default is `60`.
- `T`: Maximum timespan. Default is `3.0`.
- `sigma`: Standard deviation of observation error. Default is `0.075`.
```
