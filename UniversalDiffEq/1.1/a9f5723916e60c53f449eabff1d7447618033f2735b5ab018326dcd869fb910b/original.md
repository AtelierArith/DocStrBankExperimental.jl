```
LorenzLotkaVolterra(;kwargs)
```

Create a sample dataset using the Lorenz Lotka-Volterra model as its process model:

````
```math
rac{dx}{dt} = rx(1-rac{x}{K}) - lpha xy + gz\
rac{dy}{dt} = 	hetalpha xy - my\
rac{dz}{dt} = l(w-z)\
rac{dw}{dt} = z(ho-s) 0 w\
rac{ds}{dt} = zw-eta s
```
````

and an observation error following a normal distribution with mean 0 and standard deviation σ_{obs}.

```
# kwargs
- `plot`: Does the function return a plot? Default is `true`.
- `seed`: Seed for observation error to create repeatable examples. Default is `123`.
- `datasize`: Number of time steps generated. Default is `60`.
- `T`: Maximum timespan. Default is `3.0`.
- `sigma`: Standard deviation of observation error. Default is `0.075`.
```
