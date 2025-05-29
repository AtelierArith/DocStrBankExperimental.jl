Constructs a ME-NeuralFMU where the FMU is at an arbitrary location inside of the NN.

# Arguments

```
- `fmu` the considered FMU inside the NN 
- `model` the NN topology (e.g. Flux.chain)
- `tspan` simulation time span
- `solver` an ODE Solver (default=`nothing`, heurisitically determine one)
```

# Keyword arguments

```
- `recordValues` additionally records internal FMU variables
```
