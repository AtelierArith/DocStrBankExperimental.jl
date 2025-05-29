```
generate_dosing_callback(I; S1)
```

Returns a DiscreteCallback implementing the dosing events in intervention matrix `I`.

# Arguments

  * `I`: Matrix with rows containing events with time, dose, rate, and duration columns.
  * `S1`: Scaling factor for the doses. Used to get the dose in the same unit as model parameters. Default = 1.
