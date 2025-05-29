```
MonteCarloLogger()
MonteCarloLogger(T)
```

A logger that records acceptances in a Monte Carlo simulation.

The logged quantities include the number of new selections (`n_select`), the number of successful acceptances (`n_accept`), an array named `energy_rates` which stores the value of $\frac{E}{k_B T}$ i.e. the argument of the Boltzmann factor for the states, and a `BitVector` named `state_changed` that stores whether a new state was accepted for the logged step.
