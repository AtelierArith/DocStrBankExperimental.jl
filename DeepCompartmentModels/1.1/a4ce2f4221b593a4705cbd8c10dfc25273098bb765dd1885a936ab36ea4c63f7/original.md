```
LowDimensionalNeuralODE(ann, node; kwargs...)
```

Convenience function for constructing low-dimensional Neural-ODE based models. This simple implementation learns a model according to:

```
du/dt = node.u(u) + I * node.t(t)
```

Where the model learns the system dynamics based on the previous state u and  current time point t. See [bram2023] for more details.

# Arguments:

  * `u`: NeuralODE taking `u` as its input.
  * `t`: NeuralODE taking `t` as its input.
  * `kwargs`: keyword arguments given to the NeuralODE constructor.

[bram2023] Bräm, Dominic Stefan, et al. "Low-dimensional neural ODEs and their application in pharmacokinetics." Journal of Pharmacokinetics and Pharmacodynamics (2023): 1-18.
