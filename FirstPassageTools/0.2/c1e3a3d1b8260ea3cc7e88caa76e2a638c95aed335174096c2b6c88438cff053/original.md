```
setup(path::String)
```

Setup a first-passage time problem by specifying a path to a .csv file containing the transition.

The .csv file should have the column names "condition", "from", and "to". Currently, the transition rates are set to be equal to the number of states in each condition. This keeps the processing times comparable between conditions, and when fitting the scaling parameter τ, that τ represents the transition rate per jump.
