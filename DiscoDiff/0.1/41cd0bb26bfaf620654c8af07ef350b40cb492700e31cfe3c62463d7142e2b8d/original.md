```
sign_diff(Number, [steepnes]) -> Number
```

Implements the sign function in the forward pass.  It is 1 if x > 0, -1 if x < 0 and 0 if x = 0. The derivative is taken to be the tanh. An extra parameter k controls the  steepnes of the sigmoid, default is 1.
